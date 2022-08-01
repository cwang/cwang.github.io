---
title: "Opinionated Patterns/Practices in Java Development and Deployment, 2017 Edition"
date: 2017-03-10T00:00:00Z
draft: false
categories: ['Java', 'Take-away']
---

## Caveat
Java and JVM have changed a lot since this article was written. 

![Unsplash | Kenny Eliason](/kenny-eliason-uEcSKKDB1pg-unsplash.jpg)

**Read with a nostalgic lens.**

## Development

### In general
- Use Java 8 and use it well
- Use an IDE and use it well
- Prefer Enum over defined constant/variable
- Prefer standard/built-in exceptions over custom/user-defined ones
- Almost always use java.util.concurrent and its subpackages instead of Thread/Runnable
- Use Interface only when it is absolutely necessary
- Use Package structure wisely to avoid spaghetti code
- Master a build tool and stick to it

### For application developers
- Choose libraries/frameworks wisely (but still prefer the use of libraries/frameworks over BYO)
- Write your code so that it can be as framework-agnostic as possible (or if a framework is to be used, embrace it and its dependencies whole-heartedly)
- Write meaningful tests, i.e. test against things that may go wrong because of your code

### For library/framework developers
- Consider supporting earlier versions of Java (e.g. 6 and 7)
- Have as few dependencies as possible 

### Documentation
- Have the stamina to support it for as long as possible

## Deployment

### In general
- Fat jar is your friend
- Apache Tomcat is good enough for pretty much anything in a web environment
- For JVM tuning, know your application and then RTFM
- Know-it-all (or a bit of everything) helps in DevOps world

### Cloud vendor
- Just use AWS
- AWS Lambda is great, but not so great for Java

## Misc.
- To grasp Java the language, consider studying for an OCP exam
- Look beyond Java and JVM for new patterns and trends but think critically
- Communication (and other soft skills) sometimes is more important than programming skills
