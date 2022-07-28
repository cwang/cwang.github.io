---
title: "JSR-223 Java Scripting API - a Real World Use Case: Success and Pitfalls"
date: 2012-09-20T00:00:00Z
draft: false
---

Despite the fact that Java 6 is fast approaching EOL, certain newly added features seem to still remain relatively unknown or unused; JSR-223, the Java Scripting API is probably one of those least mentioned in “What’s New in Java 6” type articles. In this article, we will touch on a real-world use case of the new API and its programming model. Hopefully towards the end, the readers can have a better understanding of the feature and form their own opinions about the suitability for use of the API in their own projects. 

![Unsplash | Kevin Ku](/kevin-ku-w7ZyuGYNpRQ-unsplash.jpg)

## Why Java Scripting API for the project

At Volcube, we run a SaaS-based training environment for financial Options trading. The software includes a trading simulator with comprehensive trader performance analysis and an application for training oneself in the theoretical knowledge in the form of a series of small web-based quizzes. Each quiz is a mini-game in Volcube terms and can be re-attempted indefinitely as each time it will ask a different question, similar to how a typical number guess game works. Historically, It started with our client-facing product experts writing basic Python scripts, runnable as single-user console-based programs, to illustrate the ideas for various quizzes to our development team, and we then decided to move it to a web-based environment with multi-user access. Looking back, there were a few coincidences that put us in the situation where using Java Scripting API seemed like an attractive option:

- The polyglot development environment at Volcube where not only Python but other languages such as Groovy are in common use pushes us to look for a polyglot solution in the first place; Also we anticipate that there will be more mini-games being created in the future, most probably written in Python but we cannot rule out the possibility of using other languages.
- The simplicity of being able to run a scripting language based mini-game standalone and test it out instantly confirms that using scripting languages is a viable and suitable solution in this particular case and the application should facilitate that.
- The software is already on Java 6 which officially supports the Scripting API, and the recent release of Jython 2.5.2 already includes the scripting engine for JSR-223.

## Project architecture and code structuring

After we set out to use Java Scripting API, the next immediate issue is how to design the application so that those script-based games can be loaded and then played by users. The approach we take consists of 

- An application framework which handles user interactions and loading the games;
- A number of games each of which resides in individual script files;
- Between framework and games, a game interface to interconnect and facilitate the loading and playing.

The framework part is written in Java 6 with Spring (MVC and JDBC), with plain HTML/JSPs in view layer and backed by a conventional SQL database. Functionally it includes user authentication through Volcube single-sign-on service, form handling for gameplay and database operations for scorekeeping. The game interface is not difficult to define, the code snippet below being a simplified example:

```
package com.volcube.minigames.misc;

public interface NumberGuess {

	String getHelp();
	
	String getQuestion();
	
	int getAnswer();
	
}
```

The games themselves are as described previously. All are written in Python and saved in individual .py files. What’s different now is that each Python game is made framework-aware by importing and extending the game interface defined above, as shown in the next code snippet:

```
#! /usr/bin/env python

from com.volcube.minigames.misc import NumberGuess
import random

class NumberGuessClass(NumberGuess):

	def __init__(self):
		self.numbers = [1,2,3,4,5]
		self.result = 0

	def getHelp(self):
		return "You need to say a number among " + numbers + " and we will tell you the answer"

	def getQuestion(self):
	   if self.result == 0:
	       self.result = random.sample(self.numbers, 1)[0]
	   return 'What is the number?'
		
	def getAnswer(self):
		return self.result
```

## Sample Java Scripting API uses

All the magic happens in javax.script package, at least on the surface and in our code. The code snippet below shows that a few lines of Java can load and run the script from a file,

```
ScriptEngine se = new ScriptEngineManager().getEngineByName("jython");
CompiledScript cs = ((Compilable) se).compile(new InputStreamReader(this.getClass().getClassLoader().getResourceAsStream(“numberguess.py”)));
cs.eval();
```

Above is what we use in the project, through compiling and then evaluating; An alternative is to run the script directly,

```
ScriptEngine se = new ScriptEngineManager().getEngineByName("jython");
se.eval(new InputStreamReader(this.getClass().getClassLoader().getResourceAsStream(“numberguess.py”)));
```

More details about different ways of running scripts will be further discussed in “Pitfalls to avoid” section of this article. 

Of course, the underlying heavy-lifting is down to the use of JSR-223 compatible script engines, and in our case the one provided by Jython library for Python language. Similar to how a typical JSR spec works, programmers do not interact with underlying script engine implementation directly; using classes/interfaces in javax.script package should be enough for most use cases. 

The code can also be made smarter by having a mapping between file suffixes and script engine names so that depending on each script file’s file extension/suffix, the code can use appropriate script engine. Java 6 has a built-in script engine for Javascript based on Rhino, named “js”; Other script engines such as JRuby and Groovy are available through 3rd-party libraries, similar to how Jython works above.

## A success story

Overall we have been very satisfied with the stability and performance of the implementation since the deployment to production nearly one year ago. As part of the development team for this project, we were delighted to offer a paid internship to a 2nd year Computer Science student at the University of York; with some core Java programming experience, he did a brilliant job in getting it off the ground to a successful V1, which goes to show that the use of Scripting API is easy to follow. The project has also undergone a few minor refactorings such as adding a new league table for players and during the course, the script engine remains solid throughout.

The most obvious advantage, in the polyglot development environment at Volcube is that it enables a clear separation between game authors and application developers by drawing up an interface for games to be loaded as cartridges, independent of the language being used, as long as it is supported by the corresponding script engine. The interface remains to be simple but powerful enough to convert a single-player, console-based game to a multiplayer, web-based one without code change within the game. The solution is also extensible as game authors have the freedom to use any JVM-supported language to write any game that is also easy to test in a standalone way. 

It also brings in positive changes for operations. Because of the nature of application framework/infrastructure code which does not change often, we have been able to update games on-the-fly thanks to the dynamic nature of underlying implementation using individual script files loaded periodically into the application. We can pull or add a game, as well as updating one without interrupting user experience even under a non-clustered deployment environment. 

## Pitfalls to avoid

It goes without saying that we inevitably hit some unexpected issues or difficulties, some of which are caused by our own lack of understanding of the API initially. 

One area we had a concern about in the very beginning is performance and it did come to bite when we write code to load a script file and evaluate the dynamic language code in it. Consider the code snippet below,

```
@Test
public void testRun() throws Exception {
	int loop = 1000;

	long t = System.currentTimeMillis();
	for (int i = 0; i < loop; i++) {
		int x = 1 * 2;
	}
	System.out.println((System.currentTimeMillis() - t) + "ms for " + loop + " java calc");
	// output is ‘0ms for 1000 java calc’

	ScriptEngine se = new ScriptEngineManager().getEngineByName("jython");
	String code = "x = 1 * 2";

	t = System.currentTimeMillis();
	for (int i = 0; i < loop; i++) {
		se.eval(code);
	}
	System.out.println((System.currentTimeMillis() - t) + "ms for " + loop + " jython intepreted calc");
	// output is ‘1646ms for 1000 jython intepreted calc’

	CompiledScript cs = ((Compilable) se).compile(code);
	t = System.currentTimeMillis();
	for (int i = 0; i < loop; i++) {
		cs.eval();
	}
	System.out.println((System.currentTimeMillis() - t) + "ms for " + loop
			+ " jython compiled calc");
	// output is ‘24ms for 1000 jython compiled calc’
}
```

A test run shows that the difference in speed is huge between the two approaches and it is clear that a compiled run is much faster than an interpreted run (and native Java code runs the quickest, unsurprisingly). (This is not a scientific benchmark but it reveals some interesting numbers.)

Another cause for concern is around type conversation between Java and a JVM-supported dynamic language. In this project so far we have only used Python (and therefore Jython) with which the conversion between list and array is something we were not sure about. Only after experiments, we felt more comfortable with certain good practice and one notable conclusion we came to was to use Java arrays if possible which is compatible with Python native array type; Otherwise we had to ask game authors to import and use Java native classes such as List in their Python code, which is not as elegant as we wished but guarantees the compatibility. More about arrays can be found in Jython User Guide.  

Last but definitely not the least is the slightly different runtime behaviour between Oracle JDK and OpenJDK in JSR-223 implementations. We started with Oracle JDK/JRE 6 installed on all environments across dev, QA and prod stages but we did not ask every developer to use Oracle JDK 6 only on their development machine. That, unfortunately, coincides with Ubuntu’s withdrawal of shipping Oracle JDK and as a result, OpenJDK became the default and was subsequently installed on some of our development machines. In theory, it should be 100% compatible as it passed the TCK test but when it goes to the support of scripting languages, it did not appear to be 100% compatible. This stackoverflow question thread is a perfect example of how and why it is the case. The solution is simple, be militant and particular about a single JDK to be installed consistently on all development and deployment environments; in our case, that is Oracle JDK 6. 

## Closing thoughts and moving forward

Looking back, the motivation for us at Volcube to use the Java Scripting API in this particular project is mainly to enable collaboration in a polyglot programming environment. It also allows future development to be conducted in other different scripting languages as long as they are supported by corresponding script engines in Java. There is perhaps another more common and realistic use case: for organisations where there are legacy scripts written in languages that JVM can support, this would be an ideal solution to protect past investment and avoid rewrite cost. Given our experience with this solution, we think it is production-ready and suitable for the day-to-day running of a mission-critical application. 

Moving forward in Java and JVM development, there is a new project on the horizon that provides even better support for running languages other than Java on JVM, the Da Vinci Machine project under the umbrella JSR-292. The promise is a lovely one, and it puts other JVM languages in almost the same position as Java which has long been the first and only officially supported language running on JVM. Java 7 has carried some of the improvement such as the introduction of invokedynamic in HotSpot JVM, which serves as a solid ground for more innovations in this area. More information about this new feature in Java 7 can be found in a well-written article published on Oracle website.
