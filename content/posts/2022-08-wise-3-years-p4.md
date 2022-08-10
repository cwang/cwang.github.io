---
title: "Reflections on 3 years of (Transfer) Wise | Part IV: The Engineering Organisation"
date: 2022-08-13T00:00:00Z
draft: true
series: ['Reflections on 3 years of (Transfer) Wise']
categories: ['Lessons Learned', 'Startup']
---

![beaworld](/wise-hackathon-2018.jpeg)

(^ Hackathon 2018 | Conversion Team - Daniel, Karl, Urgo & Michael  ^)

It would have been a waste of opportunity NOT to talk specifically about the engineering organisation at Wise, as this is a topic close to my heart. I could not have had a better learning experience living and breathing the changes in those years when the organisation reacted to the growing demand.

I care deeply about Wise, in particular, its engineering organisation and because of my full visibility, there will inevitably be some candid opinions about what could be done better. 

## Engineering organisation evolves

As this [blog post](https://medium.com/transferwise-ideas/from-2-founders-to-1000-employees-how-a-small-scale-startup-grew-into-a-global-community-9f26371a551b) summarised, when I joined Wise in 2018, there were approximately 150 engineers globally out of a 1,000 total headcount. Despite London being the headquarter, it was only the second largest engineering base after Tallinn, with Singapore and Budapest trailing, followed by New York. Just before I left, the engineering headcount hit 350 out of 2,000 total and London became the largest engineering base.  

As in any engineering organisation, getting people through the door and getting them productive are two important tasks to achieve growth. To achieve engineering headcount doubling from an already large base, those two tasks needed great execution. 
- For hiring, in-house recruitment was beefed up; the interview process was iterated on, and the volume of interviews an engineer went through weekly was high. I was doing one interview daily for some months at peak. 
- For onboarding, it started with an unintentionally sink-or-swim approach, i.e. not much effort, to some structured plans adopted by teams. It was still disjointed, down to individual teams where new joiners join. There were talks about Facebook-style bootcamp for new hires company-wide but never realised. 
- To broaden intakes, internship and graduate [programmes](https://www.wise.jobs/early-careers/programs/) were formed and improved over the years. Apprenticeship was explored too. I was full of hope for that development and did my part to help out.
- Attrition remained low, which helped headcount growth. I put it down to a generous stock options plan pre-IPO, which was probably the best among tech companies in Europe at the time, coupled with a decent engineering culture.  

The engineering organisation felt close-knitted, despite geo-distribution. Encouragement of travelling between offices pre-Covid helped, plus a healthy amount of people relocated between offices. That was not to say that each base did not have its own engineering culture. But my view was that it was much to do with the types of engineering work in each office. For instance, Tallinn was heavy on backend and platform including data initially which shaped their culture early on; London, on the other hand, was a mix of mobile/web and some backend, focused on customer-facing products and only, later on, more platform and data people joined. 

New teams were constantly being created, some spun off existing teams (team split) and others formed organically. There was a 3-person team rule: you only became a team if there were 3 or more people in the team. It made team split a more viable approach to forming new teams. 

Engineers switching teams had become a norm lately. It was offered to people who might have stayed in one team for 3-4 years to give them a fresh context to work in, which worked most of the time. It was also used as a last-ditch attempt to rescue some new hires who found it difficult to settle into their initially assigned teams. It proved to be less effective in retention and therefore became less often.  

[Spotify Model](https://www.atlassian.com/agile/agile-at-scale/spotify) was adopted loosely, and I wrote a [blog post](https://www.wise.jobs/2020/08/05/guide-to-engineering-organisation-at-transferwise-2020-edition/) in 2020 to give an overview of how Wise adapted the model, which in my biased opinion, is still worth a read.  

Alvar also gave a talk in 2019 titled [Scaling Autonomy](https://www.slideshare.net/alvarlumberg/scaling-autonomy-in-a-fintech-unicorn-wearedevelopers-2019) which is a point-in-time overview of Wise’s engineering organisation at the time.

And [product engineering principles](https://medium.com/transferwise-ideas/product-engineering-principles-at-transferwise-46a12a47e758) Harsh mentioned in 2016 still ring true.  

## Sensible approaches prevail

One noticeable cultural highlight of my time at Wise was sensible people up the down the organisation making sensible decisions. 

I credited it to the bottom-up operational model that I explained in Part II, as a result of autonomy. People who had the greatest visibility in subject matter were making decisions and were not afraid to hold their ground firm when facing different opinions from others who might base their views more on experience, and less on visibility because of their distance from the subject matter. 

There were also some organisation-wide, top-down or sideway pushes but to get the buy-in from teams, being sensible and practical was crucial. No product teams would stop what they were doing for a one-month re-architect simply because the organisation’s architecture was shifting; however, they would be willing to make incremental, small-scale changes in a divide-n-conquer way to eventually arrive there. One exception was probably the push to transition from monolith to microservices, which did require a stop-the-world approach at times. It was also a sensible top-down initiative that all the engineering team bought in. It had been a painful and long transition but we as the engineering organisation came out on the other side with a huge sense of achievement, as shown in Yuriy's [blog post](https://www.wise.jobs/2020/05/21/transferwise-stack-2020-edition/). Again it was common sense and doing the right thing at the right time.  

It boiled down to a strong product engineering culture too. It went without saying in product teams. Even with platform teams, deciding what to build was always challenged and debated, which I found healthy.   

## When mission-driven and autonomous, people do their best work

As mentioned above, product teams as the operational unit that is closest to the customers naturally benefited from the autonomy within a mission-driven, values-guided operational framework. As for individuals, i.e. engineers in the context of engineering organisation, it helped them do their best work. 
- It helped them focus on what mattered the most - building products for customers. Many organisations advocate engineering-driven culture but sometimes lose sight of the fundamental: engineering function needs to deliver values, and engineering-driven is a means to reach that, not the end goal. 
- It let their voice be heard within their teams, as well as cross-cuttingly within the engineering organisation, because of the autonomous nature. Engineers are creative and tend to be independent thinkers; they would love to be working in a culture that not just encourages but pushes them to their best.
- They benefited from constant feedback from their peers too. The motto “strong opinions weakly held” was widely accepted across the engineering organisation. Although the reality was more on the “strong opinions” side given the autonomy at Wise, it did not stop constructive feedback from flowing.
- Lastly, perhaps the phenomenon that I liked the most, was engineers going above and beyond to make engineering at Wise better. This could be contributing to shared libraries and tools, coaching/mentoring others not directly connected to them in the organisational structure, or proposing and/or implementing new initiatives that would benefit the whole engineering organisation.     

A few highlights of bottom-up projects, some of which later evolved into teams:
- Developer experience and the push to dig into productivity metrics: great insight from GitHub and Prometheus/Grafana to understand engineering behaviour and performance, as a data-driven reference. 
- Feature engineering as an internal service: a bit like Optimizely but built in-house with both backend and frontend support. 

## To succeed, be an influencer (not a manager)

I should caveat what I mean by success, that is to have one’s maximum impact in getting things done in the organisation. And I’m not talking about social media influencers here, however, the effect is similar. 

Speaking of influence, sometimes it comes from one’s position - the higher it is the more power their words carry, which is especially true in a top-down, command-and-control organisation. On the other hand in any bottom-up, autonomous organisation, that position-power dynamic no longer applies. In an engineering organisation like Wise’s, you are on your own to build your reputation as a voice of technical expertise, and it’s up to others to decide whether to listen and how much to take from what you advocate. 

There were many ways to build up the influence. Being there from the beginning helped. Taking part in cross-team activities, or helping out beyond your team, was always helpful in making you known and your achievement recognised. 

## There is room for improvement too

In short, the engineering organisation at Wise was in great shape, which was further backed up by low attribution and high engagement from people working there. However in a scaling-up phase, with the influx of new joiners, as well as old hands being promoted to unfamiliar roles, there were inevitably areas that I thought worth looking into to make the organisation even better.
- Working in silos was a challenging issue. As mentioned in Part II about autonomy, with a strong bottom-up approach, teams were likely to operate in their space to achieve reliable execution and quick iteration. It almost felt like an organisational design. Some people in the organisation, me included, were acutely aware of the situation and did their part to break down that silo among teams. Having awareness was a good first step, and the OKR exercise, later on, helped too.
- Talent density could be higher. It was a subjective point of view. I didn’t consider myself being a top engineer so naturally, I expected the organisation to have more and more engineers, far better than myself to join and stay. There were great people already there who I always looked up to, but the hiring could have been better to attract more staff/principal engineers and experienced engineering managers of the same calibre during those three years while I was there.  
- New managers needed more than training. Join a company such as Wise gave many ambitious, young engineers opportunities to step up into their first engineering management roles. It was great to see but they should not be left there on their own, sink-or-swim. There has been awareness and effort to give them training and support, but I thought they needed more from their line managers to coach them. Those coaching should cover as practical as how to do 1:1, or as high level as how to diagnose issues within their teams and find solutions. This coaching should be considered mandatory, ideally driven by engineering leadership with a detailed framework.   
- Last but not least, the speed of taking action could improve. I understood the consensus in the organisation where respect and tolerance were given to every individual. But I didn’t think that it should justify slow or no action towards sometimes low-level decisions. It could demotivate people on occasions.   

(Those above were based on 2018-2021; hopefully, the organisation has made huge strides since.)
