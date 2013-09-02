---
layout: posts
title: "Redoing the whole user interface of our web application"
categories: [coding]
---
Our application didn't have its interface change since 2008. Even back then, it wasn't winning any prize for usability or design. That interface was designed, like a lot are, by the original developers. Like most developer "designed" interface, it showed a clear lack of foresight. Often, it was implemented in such a way that made it easier for the developer to maintain than for the user to use. It was easily breakable, and small changes could render whole features impossible to use.

Also problematic, it used Scriptaculous (Prototype), as that library was then integrated in the server-side framework (Symfony). Over time, as jQuery overtook Scriptaculous in both popularity and usability for the developer, the problems with this integration became more and more evident. While jQuery has a thriving plugin community, it has become tough to even find good documentation for Scriptaculous apps. See [this post](/symfony/2013/08/19/the-walking-dead.html) for more on the risks of working with an older framework.

The interface did have a lot of good qualities though. There is something to be said for its consistency across the whole application. It was, even if not always intuitive, heavily consistent in between features. The same pattern was repeated over and over and over, which made it somewhat easy to guess where you could find one functionnality or another. It was also heavily optimised for performance through its heavy use of ajax instead of a more traditionnal "reload whole page" pattern that would have been easier to setup. Interestingly too, it aimed to be a [CSS Zen Garden](http://www.csszengarden.com/) of sorts, with a custom CSS for each client. The issue with that of course, was that it demanded heavy CSS editing whenever we got  a new client, and often didn't have the hoped modularity. This meant that sometimes, functionnality that worked with one CSS didn't work with another.

For the last 5 years, we made do with it.

We still sold to some clients, still managed to train new users, and still kept maintaining the app. We sometimes tried to have some small incremental benefits, but there was a fear we could easily break the app. Not unjustified, this fear mainly stemmed from the fact that what worked with one client often failed with another.

Then in early 2012, we lost a big bid for a very big prospect. It was a brand everybody has heard of, and would have been the crown jewel of our client roster. We lost to a competitor over usability. We matched feature for feature, were cheaper, but looked harder to use - and really were harder to use to an extent. We also lacked eye-candy, which does make a very big difference, especially when you sell to marketing. The app was to be a flagship of sorts for their brand to their resellers. An ugly app hurts the brand image.

Well, that was a big wake up call.

We decided to redo everything. Our goal was to have a new interface that:
- looked modern
- allowed for some customization per client
- was easily maintainable
- was easily expanded

We ended up choosing to use [Bootstrap](http://getbootstrap.com/), as it meant we had a complete toolkit that we could adapt to the different situations we would face. We liked the look and feel, and easily could customize the look per client.

Bootstrap uses jQuery for its javascript components, which meant we would have to either make our whole app work with both jQuery and Scriptaculous or rewrite all our frontend code to use jQuery instead of Scriptaculous. I chose the second option: it would take more time, but we would end up with something more easily maintainable. While there is no automatic way to go from Prototype to jQuery, and everything has to be done by hand, it is fairly straightforward. That part took about two weeks, which left me wondering why it hadn't been done before.

Then, I set up moving from the custom CSS classes and HTML structure to Bootstrap classes and HTML. That part was the longest, and took around 3 months. The only significant hurdle was to ensure Ajax features didn't break in the move. This was actually time consuming, as our app made heavy use of in-app popins. We had created custom popin classes that enabled us to superimpose multiple popins ; Bootstrap doesn't let us do that, so we had to come up with simpler ways to let the user interact with the application. At debugging, this was the part that had the most bugs, especially since it didn't degrade gracefully: our original HTML was ok-looking when using Bootstrap, and could still be used. For the popins however, if we didn't change the behavior, it wouldn't work "as is". 

Finally, I set up customization. The idea was pretty simple: changing the color scheme for each client. Bootstrap gave us an easy way to do that. We had the user change the color scheme, and recompile the Bootstrap less files with the new color variable values when it was done. Fairly easy. That way, only colors changed, and no customization would break the app.

In the end redoing everything took about three months, for a single developer. It is not that big of an undertaking, even for a company with limited resources and was clearly worth it. It was another three months of use in production before all the wrinkles were ironed. We are currently migrating each of our clients to the new interface.

In the year since the rewrite, we have signed 4 times more clients than the year before. Of course, not all of that can be attributed to the user interface: the recession was in full swing in France before, and our sales approach has evolved greatly. Still, it certainly helped, and the original cost of redoing the interface has been recouped now.

We are all certain, if we had had that interface, we wouldn't have lost that one client.