---
layout: posts
title: "Being the sole developer at a SaaS startup"
categories: [startup]
---
I am currently the only developer at the company where work. Despite the fact that we're a tech company selling SaaS software, it's going somewhat well.
 
I am in charge of pretty much anything technical (aside from internal network, internet and phones, thank God). Around 75% of my time is spent on development of new features and R&D. The other 25% is meetings, hosting, strategy, a little pre-sales etc. 
 
The big question is productivity. We have made efforts to increase my productivity as much as possible. I'm not a sysadmin, so for hosting we used a consultant that set up our cloud in a way that is both efficient, and makes it easy to upgrades our apps. On development, I made a number of small technical migrations to increase productivity (custom CSS to Bootstrap, Scriptaculous to jQuery) and we are moving forward with new small migrations to bypass the limitations of our legacy framework. Effective continuous integration has been setup to make QA easier and faster. Some tech documentation has also been written to enable me to be as productive as possible in finding the best approach to a problem. This is a number of quick hints for some recurring problems, some UML diagrams for the most complex parts of the app as well as for the database.
 
It has also been our strategy to limit and eventually block altogether specific features our clients might want. Let me explain this one: we sell software to Enterprise(y) customers. Most of them are used to custom made software on which any change they want can be done. We don't allow that - or rather we no longer allow that. Instead, we find solutions to their problems using existing features, and sometimes develop features that are in keeping with our product strategy. There is now just one codebase, for all clients, instead of one codebase per client.
 
Also important, being the sole developer, there is no overhead. Having been in and led many teams, I know how productive a three people team would be. In theory, I should be roughly one third as productive as a team of that size. In reality, there is so little overhead that I believe I'm about half as productive as three people team. This is invaluable, and we take advantage of this. The mythical 5-minute change is possible when you're a one person team.

Is it a good idea?

Fuck no! This situation is due to difficult circumstances in our key market. This has been emphasized by the fact that our company has moved from half-product, half-service to being an actual product oriented SaaS startup. While our business model is sound, it has meant that revenu has dropped two years ago and is just now coming back to its original level. The situation is untenable long term, and my goal is to have a fully operationnal dev team in the next two years.

Paradoxically, my being handle to handle the situation has led to it carrying on. There hasn't yet been a crisis I haven't been able to handle. This has meant that increasing the dev team has been a "nice to have" - a "very *very* **very** nice to have" one might say, but has had to come after reimbursing our debts.
 
Now, everyone is aware that this situation isn't ideal for Alveos. There are a number of risks we try and mitigate. For example, I have to be able to keep in touch when on vacation. To avoid sudden critical bugs, I forbid the delivery of new features three weeks before I go on vacation.
 
The biggest risk, of course, is my leaving or worse sudden absence due to accidental death/disease/finding my true calling as a hobo - pick one. Leaving is somewhat mitigated by the three month notice that is the norm in France, but the market being what it is, finding a replacement would be difficult. Regardless, any sudden absence is a difficult risk to live with and is tough to mitigate, as hard as I try. I don't want to leave, but I also don't want to put the company in jeopardy by breaking my leg. Therefore, we have a number of contractors that are operational for development on our app that we can call if need be. This is not ideal, but it is better than the alternative.
 
My coworkers are also very aware of the "burnout" risk. It has happened to previous devs, and to me as well at a former company. I feel I'm way below my maximum working rate, to be honest, and we are keeping it as sustainable as possible.
 
Obviously, this situation can't go on forever. While budget is an issue, it is my goal to have a resilient tech team that can move faster than I can alone. Of course, given the overhead a team brings, to double productivity we would probably need to be three. We are getting interns as a start, and depending on success, we will see where that takes us.