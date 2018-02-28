---
layout: post
title:      "Sinatra Portfolio Project - Trip Planner"
date:       2018-02-28 23:05:48 +0000
permalink:  sinatra_portfolio_project_-_trip_planner
---


It’s time for my second portfolio project with Learn Verified! This one was a lot less daunting going in compared to the CLI data gem project. As much as it is helpful understanding and getting deep under the hood, I have to say that being able to use increasing levels of abstraction (Active Record’s association macros…amazing stuff) is really nice. I knew early on that I wanted to make a travel app of some kind, like a planner to keep track of upcoming trips. I had a clear idea of what I wanted the app to look like, and as a result, didn’t do as much planning on paper this time around. So, I decided to implement Trip and User models, with user accounts as required by project guidelines.

I started off by installing the Corneal gem which provided a great skeleton file structure for the project. I then created the appropriate database and model files, and set up the associations using Active Record. I went with a User has many Trips, where a Trip belongs to a User.  Once the associations were set, I tested them out in Tux, creating instances of Users and Trips and making sure that they were relating as expected. 

It was here where I ran into some difficulty with the trip’s date attribute and getting it to save properly in the database. Dates and times always make me nervous for some reason, so guess it was time (haha..get it?) to give it the proper attention and try to understand it. Basically, the date attribute wasn’t saving into the database in the way that I had hoped given a certain user input, such as when someone enters in mm/dd/yyyy. I realized that the format that the user entered would affect whether it was going to save or whether the date would be set equal to nil. Active Record would also sometimes perform calculations in an order of operations style with the improperly formatted input, which wasn’t exactly what I was hoping for… So the only format that would save into the database was if the user entered the date in a mm-dd-yyyy format or with the name of the month fully typed out. 

Additionally, I couldn’t get the flash messages to work when I required the Rack Flash gem at the top of the application controller. Somehow they would only work when I required the gem individually in both the users and trips controller, which I think defeats the purpose of having them both inherit from the application controller class.

Other than that, building out the rest of the app went pretty smoothly. And it was nice to get some extra practice with the login/logout process. I’m super excited to move onto Rails and see what comes next!
