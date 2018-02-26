---
layout: post
title:      " 1st Portfolio Project - Ruby CLI Gem - Steam Store Browser"
date:       2018-02-25 23:20:28 -0500
permalink:  1st_portfolio_project_-_ruby_cli_gem_-_steam_store_browser
---


It’s taken some time to feel like i’ve wrapped my mind around object oriented programming, but i’m finally starting to feel like i’m getting the hang of it.  I’ve been having a lot of fun being set loose, with all the skills I’ve learned in labs in the last few months, on the first of five portfolio projects.  This first project has the following requirements:

1. Provide a CLI (Command Line Interface - I.E. Way for user to interact with program via text console)

2. CLI must provide access to data from a web page. (I chose to scrape data from store.steampowered.com - Since it’s my go-to game store.)

3. The data provided must go at least one level deep, generally by showing the user a list of available data and then being able to drill down into a specific item. 

4. The CLI application can not be a Music CLI application as that is too similar to the other OO (Object Oriented) Ruby final project. Also please refrain from using Kickstarter as that was used for the scraping 'code along'. 

5. Use good OO design patterns. You should be creating a collection of objects - not hashes.

At this point my CLI gem should meet every requirement on this list.  However i’m sure since it’s my first attempt to create an Object Oriented program in Ruby completely from scratch and without any of the tests to drive me from objective to objective like in the labs, there will be a need for some refactoring. That’s okay!  I welcome any chance to improve my code and really look forward to getting to discuss it with my instructor.  As i’ve been learning, and am starting to feel more confident with my abilities, i’ve found myself willing to expand features beyond the original requirements.  
Here’s a quick tour of what i’ve coded for this project: Feel free to install the gem yourself and play with it! (Steam Browser github repo: [Link to steam browser github repo](https://github.com/mcrooks65/steam-browser))

This is the main menu - Simple, and easily expandable!

![](https://imgur.com/pCNNGYM)

Entering 1 to select “Matt’s Picks” - Brings up a list of my current top 5 recommended games.

![](https://imgur.com/nclrk8Q)

Currently there is a problem drilling down into store pages of games that require age verification.  This is one problem I haven’t figured out a solution to yet but am curious to ask my instructor about.  

Let’s select a couple games to look at the details of, how about the first two?

![](https://imgur.com/Vp4BHKu)

Beware of shameless self promotion!  (FreeHolder is the first game developed by RogueWare, an Indie Dev studio I started with my brother some years ago.) 
Currently the details you can get off any valid title on Steam are:
-Price
-Description
-Player Reviews Rating
-Genres 

There’s of course room to expand this for more details.  It would be easy enough to add other details like the names of developers and publishers, or an indicator for when there’s an active sale price on a game.

Going back into the main menu after exhausting “Matt’s Pick’s” you might want to look up some games of your own.  Well i’ve expanded on the program with a function to do just that!  The second option in the main menu is to search for a game by its title.  Let’s try ‘ftl’ for the classic indie hit Faster Than Light.

![](https://imgur.com/JMznWzU)

It worked!  Currently it will break the program if you try to search for a game that would require age verification, or if the search comes up empty.  I don’t think these would be too hard to address but at this point i’d like to see what the instructor thinks.  This feature wasn’t a requirement just an easily expandable feature thanks to the code i was already required to produce for the Matt’s Picks list.

That’s really all there is to my program.  It’s simple, but plenty could be done to enhance it and make it harder to break.  If i wasn’t so anxious to get on with the curriculum and get working towards the second project i’d start implementing other ideas like a search by game genres function that would return a list of the first 5 or 10 games associated with that genre on Steam. 
	



