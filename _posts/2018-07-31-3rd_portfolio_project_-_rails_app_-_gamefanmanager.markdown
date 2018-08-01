---
layout: post
title:      "3rd Portfolio Project - Rails App - GameFanManager "
date:       2018-08-01 03:10:54 +0000
permalink:  3rd_portfolio_project_-_rails_app_-_gamefanmanager
---


I will readily admit - Rails wasn't as easy to conquer as I first thought it might be.  As usual the labs gave me that false sense of security that I keep getting reminded can only be achieved when pressed through the guantlet of an entire project from conception to completion.  But what really made it -feel- like it would be easy is because Rails really does do -alot- of magic.  It's all designed to make things run more seamlessly and truly is far more capable of a framework than Sinatra.  It became clear rather quickly why Sinatra was really more for pet projects and Rails for enterprise grade software.  The shiny new Rails tool belt seems to make everything easier!  But man there sure are a lot of things you can do with it and thus the instruction book grows thick.  But that's okay!  We're not afraid of documentation, it only enables us to do more with our code.  And appropriately enough we were asked to do quite a lot with this project.  If you compare these specs with the last blog entry, you get a taste for the extra dimension this third project took compared to the earlier two.

1. Use the Ruby on Rails framework.
2. Your models must include a has_many, a belongs_to, and a has_many :through relationship. You can include more models to fill out your domain, but there must be at least a model acting as a join table for the has_many through. Make sure that the join table contains at least one user submittable attribute.
3. Your models should include reasonable validations for the simple attributes. Models should defend against invalid data.
4. You must include at least one class level ActiveRecord scope methods. 
5. Your application must provide a standard user authentication, including signup, login, logout, and passwords. 
6. Your authentication system should allow login from some other service. Facebook, twitter, foursquare, github, etc...
7. You must make use of a nested resource with the appropriate RESTful URLs. Additionally, your nested resource must provide a form that relates to the parent resource. E.g. /profiles/1/pictures
8. Your forms should correctly display validation errors. Your fields should be enclosed within a fields_with_errors class and error messages describing the validation failures must be present within the view.
9. Your application must be, within reason, a DRY (Do-Not-Repeat-Yourself) rails app. Logic present in your controllers should be encapsulated as methods in your models. Your views should use helper methods and partials to be as logic-less as possible. Follow patterns in the Rails Style Guide and the Ruby Style Guide.
10. Do not use scaffolding to build your project. Your goal here is to learn. Scaffold is a way to get up and running quickly, but learning a lot is not one of the benefits of scaffolding. 

It's quite a bit more to chew on than before!  But after masticating for the last two months on this project, it's time to move on to even bigger fish in the next section - where we'll be adding JavaScript on top of Rails!  So let's run through this project and i'll explain my creation from start to finish, first by going over what Rails is, and reiterating how much more dynamic and expandable it is and why its considered enterprise grade.

Ruby on Rails, is a server-side web application framework written in Ruby under the MIT License. (The MIT license is the standard of open-source software, community developed and maintained) Rails is a model–view–controller (MVC) framework, providing default structures for a database, a web service, and web pages. Here's a look at the file structure next to the last project (Sinatra project up top, this Rails project below, notice how many more folders there are than just the model controller and views folders):

![](https://i.imgur.com/xldqvBD.png) 

When I first saw this I felt a bit intimidated, but the fact is the majority of those other folders aren't neccessary to create what I already could in Sinatra, or for that matter meet the specs of this project, however, Rails shows just how much more dynamic and expandable it is and why its considered enterprise grade software.  Unlike in Sinatra where I created the file structure by hand, we have this handy generator in Rails that stubs out all the basic files and folders, depending on specifications you make.  Rails makes doing things like creating database migration files, integrating a new model and its associated controllers and views much easier.  Added advantage of not needing to reboot the server everytime you change a line of code and you've got a fantastic environment to build up any project.  

So what did I do with Rails?  Well what else, another game related project, i figured i'd add one layer on top of the specs of the old one, since we needed not just 2 models but 3 now, to satisfy the has_many through relationship requirement.  So instead of just Developers and their Games, we now have Fans.  A Fan can only choose games that they like, but Developers in turn then have_many Fans through Games.  This is essentially the Ruby language used to set up database relationships and the methods available to the programmer:

![](https://i.imgur.com/bM7JGzr.png)

This is what makes Ruby much easier to learn, it's closer to plain English than most programming languages.  Those lines of code make it easy to reach into my database through a Developer object and pull up a number of how many Fans they have for each of their Games.  Most of what web applications do is deal with information a user might want to pull from database, and efficiently getting at that information is really pretty simple in Rails.  Validations are also rather easy to set up in Rails, once again using easy to understand language:

![](https://i.imgur.com/vyXIKgA.png)

With these lines loaded into the model, the database will always validate data for these parameters before making any changes to it.  This is what prevents people from submitting forms with bad or missing data into a database.  This will flag the error for the user and let them know what to fix.  Rails also gives access to these errors so that you can easily display them in the view, like this:

![](https://i.imgur.com/DQ8s1MR.png)

Unlike in the last project where there was only one way to authenticate, this time we needed to devise a custom authenitcator plus the ability to authenticate using an outside service (in my case i chose GitHub).  This way the user can use outside authentication to login to my web application:

![](https://i.imgur.com/PtXwaJa.png)

Whichever way they login will give them a valid session token until they sign out.  Here's a look at the Developer show page:

![](https://i.imgur.com/9slMa3Q.png)

From this page a Developer can add Games or view the current games they've added to the database.  Here's a look at the FreeHolder Show page, note the RESTful routing in the url bar.  This is the modern standard routing for building websites.

![](https://i.imgur.com/O9JX8QN.png)

I created a Fan Tally page where you could see how Games and Developers stack up against eachother.  I didnt' pupulate the DB with a ton of data but this gives you an idea:

![](https://i.imgur.com/3IXbp6A.png)

Since that covers the majority of things I think i'll leave it at that.  I'll leave the Github repo here for curious Rails devs to pull apart.  The repo is here: [https://github.com/mcrooks65/gamefan-manager](https://github.com/mcrooks65/gamefan-manager)

Now onwards and upwards!
