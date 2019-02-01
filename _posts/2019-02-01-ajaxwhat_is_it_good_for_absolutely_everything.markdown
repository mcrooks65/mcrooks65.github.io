---
layout: post
title:      "Ajax - What is it good for?  Absolutely everything."
date:       2019-02-01 04:34:51 -0500
permalink:  ajaxwhat_is_it_good_for_absolutely_everything
---

Though typically I do thorough breakdowns of my project for these blog entries, i thought instead i'd break down the subject matter at hand, since this project is actually an extension of the last project, the Rails project - GameFanManager.  The goal of this project was to take that current working rails website, and extend it with Ajax.  That wasn't going to mean much to a reader who might not know what that is, so without further ado, let's dig into what Ajax is and why it's so darn great.

Let's go back before 2005 - a time before Ajax.  A time before webpages were so dynamic and interactive, when broadband was just starting to become more common, and with greater bandwidth, users demanded more from websites.  Ideas abound!  But there was one thing jamming up all of the great innovation we've come to enjoy on the average modern website.  In the 'beforetimes', users would often have to wait tens of seconds for a server to respond to their request before they could proceed with whatever they were doing on a site.  Alas, the user was constrained by the speed at which the server could crunch their typical http request, and then wait for a html page to be returned from the server.  But then came AJAX, ushering in the webapp, the ability to give the client more than just html to serve a user, but an interactive engine that could do all the crunching on the clientside, saving valuable server-side resources, while much less intrusive XML could fetch and make adjustments to server data as neccessary.  This idea was all tied together using JavaScript.

Ajax is shorthand for - Asynchronous JavaScript + XML.  It is not a technology itself, but several technologies being merged together in fundamentally new ways to give tons of new possibilities to what can be done on the web.  (New for 2005, still standard today.)  For example, social media feed scrolls bringing fresh news, their 'like' and comments sections, are all created using Ajax.  If Facebook were around before Ajax, everytime you clicked to 'like' something it would have to reload the entire page.  Ajax makes browsing the web far more data effecient and enhances the user experience by simply not wasting their time.  To borrow from the original source, the blog post that started it all, (https://adaptivepath.org/ideas/ajax-new-approach-web-applications/) these are the five things that Ajax incorporates:
-Standards-based presentation using XHTML and CSS;
-Dynamic display and interaction using the Document Object Model;
-Data interchange and manipulation using XML and XSLT;
-Asynchronous data retrieval using XMLHttpRequest;
-JavaScript binding everything together.

![](https://adaptivepath.org/uploads/archive/images/publications/essays/ajax-fig1_small.png?timestamp=1549011366669)
The traditional model for web applicaitons(left) compared to the Ajax model (right)

The start-stop-start nature of web browsing pre-2005 has since been largely solved by the introduction of the Ajax engine intermediary.  Though it is counter-intuitive that adding an extra layer to an application would make it more responsive instead of less, it has completely evolved the usability of the internet.  If you can interact with it without refreshing the page, that's Ajax.  Did Google Suggest automatically fill in your query while suggesting 10 different other possible queries?  That's Ajax at work too.  Same with Maps and Gmail.  Web applications we all find ourselves using on a daily basis.

It's by no means simple to learn, but once one gets familiar with Ajax, there is little that can't be done with a webapp, and that has become abundantly clear to me during the couse of this project.
