---
title: "Lessons learnt in 10 years of Volcube"
date: 2021-01-30T00:00:00Z
draft: false
---

I vividly remember the early summer of 2010, when I started writing code for a stealth-mode startup. There was no name but we used a code name “project volt”. Fast forward 10 years, Volcube, as it later became known, was sold to our joint venture partner of 5 years. 

Looking back, I count myself lucky as 90% of the startups fail; We managed to build a leading product in the field from scratch, with a number of customer segments spanning many countries. It was certainly not a failure but I would not call Volcube a huge success either, at least not at the level exemplified by some other SaaS product companies featured in the limelight. 

One thing I know for sure is that I have taken many learnings from being the founding CTO for those 10 years of Volube. It would be a shame if I did not write them down and share with people who may find them useful. So here go the lessons leant and the hope is when you find yourself in those situations, you are more informed and/or better prepared. 

I will delve into a few common topics during a startup lifecycle, in the context of Volcube, in this three-part series. The first part is for product and growth; followed by engineering and design; and then any other topics. Each part ends with a *what-we-could-have-done-differently* question to give some food for thoughts.    

## Part I: Product & Growth

### Product: (the small) addressable market size
Volcube was the best product in the space it occupies, which was a market-making trading simulation and education for financial options. This may sound like a boast but let me point out the fact that it is in such a niche market, which is combined with another fact that we did well in bringing a good idea into reality. Here comes the biggest learning though: always target a market with large addressable size. You might have a false sense of security and comfort in seeing your product gaining traction in a small market; however, you would touch the ceiling soon and as a result, you would not benefit from the biggest killer feature in any SaaS business: the economies of scale. We were lucky that there was money around in this niche market, therefore our customers could afford a much higher unit price we charge compared to a typical SaaS product. But a small market means a small number of customers, which in itself is a risk when one or two larger customers stop paying. 

### Product: (paying) customers versus (non-paying) users
This is a typical scenario of paying customers who organise the learning for non-paying users who use Volcube to learn. In some cases, the interests are strongly aligned (a trading firm would be more than happy to invest in their graduate intakes); in others, not so much. 

Despite the paying-user imparity, as a highly technical product and the best in the field, Volcube benefited from expert users in customer organisations, who advocate for the purchase. In general, our customers’ purchases are affected only by their available budgets.

On the user side, they are high-intent fast learners. What we found is a contradicting picture in terms of usage: they are extremely sensitive towards any bugs in the product especially those affecting their evaluated performance (scoring); they are also highly tolerant of inconvenience introduced by user experience design, as long as it doesn’t affect their scoring. To gain user satisfaction, we kept a quick turnaround on bug fixing. And as mentioned later, we also refrained from making further investment in design.

What’s interesting was that against common product building advice of always listening to customers, we had clear ideas of what to build from day one for one of the co-founders was a domain expert who had also been in our customers’ position for many years prior. This was a scratch-your-own-itch product after all.   

### Growth: bootstrapping versus venture capital
We bootstrapped Volcube, which had become profitable since 2nd year in business. It is simple math for a B2B SaaS business: making more sales and not overspending, which we followed. In a niche market, it worked. We had never talked to any VCs because there had been no need. 

Hypothetically, things could have taken a turn if we did take VC money: we could target other financial instruments using the same piece of technology as the foundation; we could target retail investors with a B2C play. One thing for sure would be the drive to hyper-growth, with a go-big-or-go-bust attitude. I am afraid it would probably not lead to any exit as Volcube had, which would have not been considered worthwhile for venture-backed business.

On the other hand, a leading product in a niche market provides a sustainable revenue stream for a lifestyle business. If a steady cash flow is something you’re after then there’s nothing wrong with pursuing such a business model.        

### Growth: joint venture
This is an interesting one. Not many startups would ever come to this and it was certainly new to us at the time. It broadened the appeal of the product and took Volcube to markets we never knew existed. There had been mistakes made by us too. In the end, it led to a smooth exit thanks to the fact that both parties had been in business together for a while. 

As it is clear that what the joint venture solved for us was sales, we should have invested more in growing our own sales team in hindsight.

### Product & Growth: what we could have done differently

## Part II: Engineering & Design

### Engineering: take on technical ~~debt~~ options and make lucky guesses
Volcube is all about trading options and I think it is a closer metaphor than debt in making engineering trade-offs. Debt will have to be repaid; options can be taken up but there is no obligation. It could be useful taking a step back to imagine a product 1/3/5 years down the line, and what would be required engineering-wise that current design would make amends. Past experience with specific tech stack such as seeing them supporting a similar product on a much bigger scale could also help make rational decisions instead of for short-term gain. This led to making educated guesses, which were with low up-front cost and high potential to be used more extensively in the future. 

A case in point was the use of a single-sign-on system which the whole product architecture was then centred around. It was overkill in the beginning although there had been tell-tale signs already such as the need to integrate a WordPress (PHP) component with a Java application. There was also the projected growth where we could have more engineers working on different components/services/applications loosely connected with the SSO system. In the end, it was a bet that paid off spectacularly as the SSO connected architecture remained as the backbone to this date.  

### Engineering: KISS and consistency
In software engineering, I like simple architectures - easy to understand, easy to reason about and easy to change. In a startup context, simplicity also means no overdesign up-front. There had been many Keep It Simple Stupid principles in action when building Volcube. 

One was our release process, which started as a simple Bash script, later evolved into a set of more complex ones. But they remained as Bash scripts and they worked. 

Another was our Cloud vendor choice after our humble beginning of virtual machine hosting: we used DigitalOcean as the main provider; plus the most ubiquitous AWS services, S3 and CloudFront. DigitalOcean was a point-n-click, easy-to-operate vendor with good customer support, which matched our belief of not to build any infrastructure piece unless we absolutely needed. If they had object storage and content delivery network at the time, we would have used them solely. 
 
Another aspect of KISS in the context of Volcube is consistency, which reduced the cognitive load in understanding the engineering aspect of the product. Take the product architecture as an example: there were different components running but they all followed the same behavioural code:
- Each followed a typical 3-tier architecture
- Each ran independently in a local development environment
- Authentication: SSO
- Authorisation: shared database
- Data integration: shared database

It helped us onboard engineers new to the tech stack, as well as gave confidence in system operations.

### Design
For all my designer friends, the disappointing news is that Volcube had never been design-led. We were very clear in the beginning about what we knew, UX-wise: a trading screen simulating the real one. Once it was decided and implemented, all the rest of the product design followed the same aesthetics (dark theme, number-heavy panels and clear navigation). There was plenty of room for improvement. However, it had never been a source of complaints from users, from which my conclusion was that we struck the right balance between cost and benefit here.  

### Engineering & Design: what we could have done differently

## Part III: AOB (any other business)

### Co-Founders: trust and complementary skills
I am grateful to have Simon as the co-founder and CEO of the business. He did everything: coming up with the idea, making big or small product decisions, even writing some code in questionable quality and most importantly, making sales. I had the easy part: building it. Having complementary skills is clearly helpful from the start.

We did not know each other prior to Volcube. But it is fair to say that we became friends as a side effect of building Volcube. I did not have a system of how to connect with trust between co-founders but to state the obvious: 
- We were both old enough to behave as adults;
- We did our best;
- We supported each other;
- We were rational and at the same time, curious.

With trust, there was little or no worry about things not on my plate, and I could make fully autonomous decisions on things within my responsibility. And it made us concentrating on the only thing that mattered: building the product and growing the business. 

### Team: remote-only and result-driven
It was such a small team to have anything meaningful to say. One worthwhile mention is our approach to remote working. While there had been people working for Volcube from many places (earlier in UK & East Europe, later solely in the UK), we never had an office. Looking back, I think we had always trusted people and paid only attention to results, instead of trying to instil and manage any processes. It was simple when it worked: people spending time individually to get work done, chatting about the work with peers and then moving onto the next chunk of work, rinse and repeat. Your experience will differ if the size of your organisation is bigger. 

### Legal: it is in every step
One thing that is rarely in the spotlight of a startup’s lifetime is access to legal services, which can only be contracted out to legal firms. We had a fair share of it during the 10 years, most notable in areas of:
- Employment (and other personnel legal advice)
- Commercial (for the joint venture as well as the exit)

It is a boring but important necessity and it costs a lot. Most of the costs are difficult to budget for as well. I don’t have any tips or tricks around it, other than bringing it to your attention for its unavoidable nature.

### AOB: what we could have done differently

## Closing

No matter what your role is, there has hopefully been something useful to take away. 

There is one more thing: I have never understood it when people say you should make it a fun experience when building a startup; maybe my definition of fun is different. What I would say is that **starting from creating a product that offers values to people (to justify the economies of its existence), and then making it as advanced as possible (to be the best in class) so people cannot say no to it wherever there is such a need**. 

You know the moment when I realised we built such a product? It was when it took us a while to reason why Volcube behaved in a way that made sense but was not immediately obvious - this product did its job better than any human who built it, with speed and ease; and that to me is a rewarding experience like no other. 

Good luck and keep building!    
