---
layout: posts
title: "The Walking Dead: the consequences of living with a legacy PHP framework"
categories: [symfony]
---

At our company, our main web app is based on Symfony 1.0, a PHP framework released in 2008. It was developped by a company called Sensio and open-sourced shortly after. It was a great framework when it came out, with all the good ideas from Ruby On Rails, CakePHP, etc. as well as great documentation, tutorials and a growing community. It is completely MVC, lets you write clean code, and does a lot of things a modern framework is supposed to let you do. But version 1.0 is clearly obsolete, and it is still our main framework. 

Since that framework came out, its subsequent versions, Symfony 1.1, 1.2, 1.3, 1.4 came out and died out. The 1.4 version came with a 3 year long term support promise from Sensio which ended in 2012. All the 1.X versions are based on the same overall architecture, and same principles. Sensio also released Symfony 2.0, 2.1, 2.2 and very recently, 2.3. which have a whole new architecture. This means a migration to those versions would all but require a complete rewrite

We still develop on Symfony 1.0. There are a number of reasons why no migration was done:
- early migrations were deemed somewhat unnecessary
- migrations are inherently risky
- the product became our main product only later on, it wasn't the company's focus in the beginning
- the company lacked a CTO able to articulate the use of spending money to upgrade a product that worked (i.e. politics)
- new "visible" features were deemed more important than technical upgrades.
- debugging was a full-time job at some point, leaving no time for an upgrade

Three years into the product's life an effort was done to do a complete rewrite of the product using Symfony 2.X. It was to be done by a consulting company, and preliminary research was already finished when I joined the company. This project was stopped for several reasons, including cost (well into the six figures, a lot for a small company) and an estimated 6-month "no new feature" period (which in my opinion would have evolved into a 9-month to one year period). The biggest issue was that our existing client base would not have benefited from the migration. As we are a SaaS company with a recurring business model, keeping existing clients is as important to us as acquiring new clients. Other issues that didn't play a role in the decision to stop the rewrite but would have been problems if we had kept going were : new software isn't as reliable as production software. New software requires new training. It was not possible to be feature equivalent in that short period, so our new application would have been behind what our competition is able to do.

So what is it like developing on a legacy framework ?

You can no longer rely on the community. What that means in my day to day job is that some problems I encounter which could be solved by Googling the issue if I was using a new framework can't be solved that way, and time is lost finding my own solution. Symfony has a great and large community, even for the 1.X versions. However, 1.0 was one of the shortest lived versions, so the main sources for tech answers (Stack Overflow, Google Groups) mainly have answers for 1.4 and 2.X. Which of course are partially or completely incompatible.

Documentation can be hard to find now. Sensio has done a tremendous job keeping its legacy documentation online and easy to find. However, due to link rot and time passing older blog posts, tips, hints and walkthroughs are often no longer available, or harder to search for. Also, training new employees and interns is much harder as tutorials and documentation haven't been updated for newer versions of PHP/Apache/MySQL.

The big one in terms of productivity: I can effectively no longer use plugins. Symfony had and still has a great plugin system, somewhat similar to Ruby On Rails gems, that enabled you to add functionnality easily. Most plugins were written for version 1.2+, no new plugins for 1.X are being written (the community for Symfony 2.X bundles however is impressive). That means I often have to develop from scratch what could have been done by just installing a plugin. I recently had to add a small CMS to our app, and had to write it from the ground up. Symfony CMSs exist of course but none are compatible with my version.

Somewhat more annoying, Symfony 1.0 used Prototype (scriptaculous) as its Javascript framework, and used it somewhat extensively. This led to all our client dside code using this library instead of today's de-facto standard, jQuery. UX advances which could require just a simple jQuery plugin have to be written from scratch. (we did solve that problem - more on that in a [later post](/coding/2013/09/02/redoing-the-whole-user-interface-of-our-web-application.html)).

This framework is not compatible with newer versions of PHP. It was written for PHP 5.2, and is compatible with PHP 5.3 but no longer works on PHP 5.4. I haven't even tried 5.5 yet. This prevents us from using the language's new features, and we can't use new some of the new libraries.

Basically I'm one third less productive when programming than I could be.

There are of course consequences for our users. While the code is quite maintainable, features and bug fixes aren't rolled out as fast as we'd like. Users have to live with the defficiencies just a bit longer than we would like them to. Speed is an other issue. Compared to Symfony 2.X, 1.X is slow. Framework overhead is really much higher than it could be. Using 2.X would probably speed execution by a factor of 2.

Apart from that though, our users don't feel the age of the framework that much. And that's why it's still more cost-efficient to keep this framework than to migrate everything. That doesn't mean I'm not making life easier for myself as we go on. More on that in later posts.

Could this have been avoided ?

Somewhat. While it was impossible to predict at the time of the release of 1.0 that Sensio would break backward compatibility with 2.X, regular upgrades to 1.1 all the way to 1.4 would have helped. The release of 2.X however would have required the complete rewrite we were unable/unwilling to finish.

**Further discussion**

Reddit discussion on [/r/php](http://www.reddit.com/r/PHP): [link](http://www.reddit.com/r/PHP/comments/1knp3v/the_walking_dead_living_with_a_legacy_php/)

Discussion on Hacker News: [https://news.ycombinator.com/item?id=6295509](https://news.ycombinator.com/item?id=6295509)