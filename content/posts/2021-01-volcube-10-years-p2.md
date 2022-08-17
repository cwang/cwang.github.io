---
title: "Lessons Learned in 10 years of Volcube | Part II: Engineering & Design"
date: 2021-01-20T00:00:00Z
draft: false
series: ['Lessons Learned in 10 years of Volcube']
categories: ['Lessons Learned', 'Startup']
---

![Unsplash | Markus Spiske](/markus-spiske-iar-afB0QQw-unsplash.jpg)

## Engineering: take on technical ~~debt~~ options and make lucky guesses
Volcube is all about trading options and I think it is a closer metaphor than debt in making engineering trade-offs. Debt will have to be repaid; options can be taken up but there is no obligation. It could be useful taking a step back to imagine a product 1/3/5 years down the line, and what would be required engineering-wise that current design would make amends. Past experience with specific tech stack such as seeing them supporting a similar product on a much bigger scale could also help make rational decisions instead of for short-term gain. This led to making educated guesses, which were with low up-front cost and high potential to be used more extensively in the future. 

A case in point was the use of a single-sign-on system which the whole product architecture was then centred around. It was overkill in the beginning although there had been tell-tale signs already such as the need to integrate a WordPress (PHP) component with a Java application. There was also the projected growth where we could have more engineers working on different components/services/applications loosely connected with the SSO system. In the end, it was a bet that paid off spectacularly as the SSO connected architecture remained as the backbone to this date.  

## Engineering: KISS and consistency
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

## Design
For all my designer friends, the disappointing news is that Volcube had never been design-led. We were very clear in the beginning about what we knew, UX-wise: a trading screen simulating the real one. Once it was decided and implemented, all the rest of the product design followed the same aesthetics (dark theme, number-heavy panels and clear navigation). There was plenty of room for improvement. However, it had never been a source of complaints from users, from which my conclusion was that we struck the right balance between cost and benefit here.  

## Engineering & Design: what we could have done differently

Surprisingly most of the initial engineering decisions stood at the test of time, so I would stick to the approach given a second chance. It was product-driven and prioritised delivery speed over technical excellence. Nothing I would have done differently. Perhaps it was the beauty of [unconscious incompetency](https://en.wikipedia.org/wiki/Four_stages_of_competence) for me as a new technical cofounder?
