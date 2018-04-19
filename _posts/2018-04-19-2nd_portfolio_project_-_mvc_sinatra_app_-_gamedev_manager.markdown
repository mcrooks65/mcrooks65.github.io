---
layout: post
title:      "2nd Portfolio Project - MVC Sinatra App - GameDev Manager"
date:       2018-04-19 05:34:29 +0000
permalink:  2nd_portfolio_project_-_mvc_sinatra_app_-_gamedev_manager
---


It's taken a lot longer to reach this point than I would have imagined but i'm anything but discouraged.  If anything every hurdle surmounted bolsters my confidence that i can indeed go the distance if i can simply continue to commit enough time and energy.  When I first approached this project i felt confident i could knock it out in a week, the previous labs, lessons and video lectures all seemed to make sense at the time of introduction and i figured it would be no problem to bring this knowledge to a fresh project.  I suppose I wasn't fully aware of just how much material i had gone through since Object Oriented Ruby and the last major project.  I'll try to summarize all the different major languages and frameworks I was taught leading up to this project.  

First I learned SQL (Structured Query Language) the universal database language that is rather fundamental to any serious web project.  After learning how DB's are created and accessed and edited, we then learned how to make our own ORM (Object Relational Map), which essentially allows us to create a Ruby object that is associated with a DB table so you can essentially access/edit a database via an object.  After making our own ORM's with much thought and effort it was then revealed  that there is already a standard ruby gem for ORM's that would take all the pain of having to code your own away called ActiveRecord.  After learning how to use ActiveRecord and confirming it was indeed easier, we were introduced to Rack, which is effectively an incredibly thin web application framework.  Working with Rack was our first chance to build web applications, and introduced us to http requests and url routing.  After all of that finally we got to Sinatra, which is a more robust, although still far paired down comparied to Rails, web application framework.  It was build on top of Rack so included everything Rack has but much more like Sessions and cookies, more advanced layout and templating with the introduction of a templating language called ERB (Embedded Ruby) which would allow us to apply Ruby logic directly into displays to create dynamic webpages.  All of this AND one more major concept would play a large role in this project: MVC.

Wikipedia.org defines MVC - Model–view–controller (MVC) is an architectural pattern commonly used for developing user interfaces that divides an application into three interconnected parts. This is done to separate internal representations of information from the ways information is presented to and accepted from the user. The MVC design pattern decouples these major components allowing for efficient code reuse and parallel development.  

A decent diagram of how MVC divides responsibilty of a web application.
![](https://i.imgur.com/zEChUMB.jpg)

(CRUD stands for 'Create, Read, Update, Delete'.)

All of the above isn't even a complete list of all of the new gems we were introduced to or concepts, but it gives a good idea of just how much was covered previous to this project.  

Without further ado, here are the requirements for the Sinatra project.

1. Build an MVC Sinatra Application.
2. Use ActiveRecord with Sinatra.
3. Use Multiple Models.
4. Use at least one has_many relationship on a User model and one belongs_to relationship on another model
5. Must have user accounts. The user that created a given piece of content should be the only person who can modify that content
6. Must have the abilty to create, read, update and destroy any instance of the resource that belongs to a user.
7. Ensure that any instance of the resource that belongs to a user can be edited or deleted only by that user.
8 .You should also have validations for user input to ensure that bad data isn't added to the database. The fields in your signup form should be required and the user attribute that is used to login a user should be a unique value in the DB before creating the user.

And what did I build to meet these requirements?  Well keeping in theme with my last project, I wanted to make sure games were once more a part of the equation, and in this case, they would belong_to a Developer which in turn has_many Games.  Thus the GameDev Manager was born.  A simple web application where Developers can create unique logins for their studios and submit games to the database to be shared with the public, all while being sure neither the public or other developers would be able to alter or delete any of the information entered by said developers.  Though not listed on the main requirements above, passwords are forbidden from being stored in plaintext on the database, thankfully the bcrypt gem makes dealing with encryption extra straightforward and so there's no problem.

Instead of plaintext, passwords are stored in the db salted and hashed.  Now even if the database is stolen, valuable user data is secure.
![](https://i.imgur.com/wIHPEB9.png)

Here are a few screenshots of what the app looks like.  It's all very basic as aesthetic was in no way a requirement, so almost no attention was paid to that aspect of this Sinatra application.

This is the root page.
![](https://i.imgur.com/GazZlKb.png)

Well I did find a pixel skele at a computer on google images to spruce up the page a bit.
![](https://i.imgur.com/Y4JldRK.png)

Developer Login Screen

![](https://i.imgur.com/0V3frRI.png)

Developer Dashboard

![](https://i.imgur.com/ojGTEOH.png)

Shameless self promotion

![](https://i.imgur.com/KP65WMl.png)

New Game Page

![](https://i.imgur.com/FOBtGzb.png)

Edit Game Page

![](https://i.imgur.com/U4BDBOw.png)

It took a long time to find my stride on this project, as Ifound myself having to constantly go back and review materials I may have rushed through, but in the end there's no better way to affirm all the knowledge than to force yourself to bring it all to the table in one massive project starting from scratch.  This might be my preferred method of learning.  I might only get a surface level of knowledge during the labs and lectures, and don't really start getting everything down until project time, or perhaps this was just a particularly cumbersome section.  Whatever the case, i'm proud of what i've achieved so far and am looking forward to seeing how Rails changes the game yet again, as it is i believe an order of magnitude more powerful than Sinatra as a web application framework.  Just what does that mean?  Tune in to the next entry to find out!







