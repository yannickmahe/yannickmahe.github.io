---
layout: posts
title: "Ensuring quality in offshore software projects"
categories: [process]
---

*Note: I was working in China for some time on French offshore software projects. The company's business model was to have a French customer facing front, with the development work done in China. One project in particular was a high priority project - as well as being a large and complex project. This is a proposal I wrote to try and ensure quality for the future developments.*

There have been a lot of times when the answer to the quality issues we've had on the project were give this response from management : "Be careful", "Failure is not an option", or even "We're just asking you to do your job". It seems that seen from France, the main reasons for our quality problems are that the China team is not careful, does not understand the needs of the client, or simply does not understand the need for quality. This could not be further from the truth.

The need for quality and the need are completely understood by the China team. This project remains the only project where every level of higher-ups can come crashing down on the China team. This has long been taken into account, and these issues are not the cause the the quality issues we face.

This project in an extremely complex one: 250 tables in the database, 1000 classes, and that's for just one app. We have no less that 30 independent apps, all interconnected one way or the other. The result is simple: no matter how careful the developer is, it is impossible for him to take into account all the risks when solving a task.

This is also a rather old project, on which around 20 different developers have worked, from the very worst to the very best of the company. This mean, whatever the level of the current developers, the project's history is the main thing impeding quality developments. The character encoding issue, for example, is first and foremost a problem due to a bad encoding choice at the project's genesis, much more than due to all the later actions that have tried to make do with this bad choice.

I am not saying the different people working on the project shouldn't be careful. Everybody is giving their all. My point is this: if the first line of defense is that nobody should make mistakes, we're on a crash course.

Quality is, before being a people issue, a process issue.

Of course, you can tell developers to "be careful" when working on files on a shared server, but you'll have much fewer problems if we use source control.

Of course, you can tell the person doing deliveries in production to "be careful" when delivering code line by line and task by task, but you'll have much fewer problems if you deliver a whole sprint at once.

The objective is therefore to have a fool-proof process - or as close as we can get.

Process improvement proposals
=============================

Development process
-------------------
Task evaluation is still a relatively important problem. We can't have feedback on the quality of estimates. It seems, however, that most estimates are two low, regardless of the person doing the estimate. To get more exact estimates, there should be time set aside to check what exactly should be done.

There should also be an effort to setup code quality measurement tools. This should allow us to follow industry-standard coding standards, which should increase the readability of the code. Current code should gradually be brought up to the standard. This would allow for a clear gain in productivity as the current codebase is, to put it simply, a huge mess.

Quality process
---------------
I believe it is foolish to try and hire more competent developers: for the last few years, the best developers in the company are move from their original team to this project's team. It is better to try and find a process that will work with the current team, or even a less competent team.

Currently, there are only 2 test levels: developer and QA engineer. The minimum to limit development side-effects would be to have 5 : developer, regression tests before commiting, full on regression testing on the regression server, QA engineer in preprod and QA engineer in prod.

To avoid problems during delivery, there should also be perfect coherence between the different environment and regression tests included in the delivery process.

Crisis management
-----------------
The project often encounters crisis caused by quality problems or unforeseen change of the use of the application (system load). Every single time, these problems are handled in an ad hoc manner

It should be easy to setup a crisis management process to handle these crisis in the most efficient way. To do so, after every crisis, the "5 whys" questions should be asked to find to root cause of the problem, and every time document a diagnosis method and a resolution process.

Furthermore, it is sometimes impossible to handle a crisis rapidly as some people do not have access to the system, or the people that know how to act are unavailable. To avoid that, there should be triple redundancy on people who have the hard-to-know info: prime, backup, fallback. That way, the probability that it is impossible to act becomes almost null.

A schedule should be set up to know who can be contaced and when. That should allow info to be available on each type of issue: system, development, etc.

Communication
-------------
Communication is a huge issue at out company, which is unavoidable for any offshore company. This is so much more of a problem on this project because there are more people working on it: 6 developers, 2 QA engineers, 1 architect, 1 Team leader, 1 html integrator, 2 sysadmins, 1 French developer, 1 project manager, 1 project director. That's not even mentionning, the General Manager, Operations Manager, Integration Team Leader or the client and its partners.

The result is simple: *nobody* know everything about what's going on in this project, and a lot of decisions are taken without knowing if they are tenable. Issue analysis can't be considered exact, and a lot of effort is spent trying to uphold what turned out to be a bad decision. One example is the release date of the last project: the client chose the date *before* seeing a schedule, which meant all the good decisions from V4's post mortem had to be ignored.

The action plan on this is simple. All the information should be centralised by the client-side Project Manager, including choices on system architecture, and the results of the CEO-level meetings. If nobody has all the information, it becomes impossible to correctly anticipate which action should be taken. Also, before decisions are taken, all the info should be obtained: production load, client imperatives, resource availability, etc. This information centralisation should be set up before new developments start.

Furthermore, contacts between France and China via Skype are not enough to ensure fluid communication. The solution implemented by numerous offshore companies is the concept of "Ambassador". Every three month one person from France should stay one week in China, and vice versa.

To make day-to-day communication easier, webcams should be used to make Skype communication more efficient.

Motivation
----------
Team motivation has a direct and evident link with quality: a passionate developer will of course do better than the one who doesn't care. Motivation is slipping the last few months. Overtime has a very bad effect on morale, especially when it is useless. Overtime should only be used with a concrete goal in mind. But, more importantly, it should be avoided and considered a last resort. Currently, overtime is being seen as the solution to all problems. This must be changed.

Risk management
---------------
Ever since V4, a primitive risk management system is in place. To go further on this, risks should be taken into account further upstream, by quantifying them in the schedule. There should also be a dedicated activity of risk discovery at project initialisation with dedicated time. This would enable us to validate risks with the people in charge of development, delivery, system, and client. The objective would be to only encounter a very small number of unforeseen problems.

Documentation
-------------
Of course, the project evolve so fast, and the client's requirement evolve so fast that it is irrealistic to believe that we can keep an up to date, complete and reliable documentation. However, it is important to pursue the documentation of processes to ensure that everybody will be able to act. This includes a complete documentation of the system architecture both in China and in France, a list of stakeholders client-side, partner-side and on our side, as well as an exhaustive documentation of the development process and the delivery process.

Continuous improvement
----------------------
To maintain client satisfaction, we should be constantly improving. To do so, we should hae a few metrics to follow, on three issues: development quality, delivery quality, and system architecture quality. We should follow closely the evolution of these metrics. This will enable us to act when the evolution goes the wrong way.

And in conclusion
=================

All this seems to be quite an investment, but as Philip Crosby has stated "Quality is free". The return on investment is such that we can consider that gaining quality will be free in the end. Quality problems are simple problems with known solutions. However, the possibility to act is not China-side. The ball is now in your court.