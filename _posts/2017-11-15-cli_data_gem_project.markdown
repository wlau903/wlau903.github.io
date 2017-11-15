---
layout: post
title:      "CLI Data Gem Project"
date:       2017-11-15 08:20:16 +0000
permalink:  cli_data_gem_project
---


My first project for the Learn Verified curriculum was to build a Ruby gem that provides a CLI, pulling data from an external web page and printing that information to the user. I have to admit, I was overwhelmed in the beginning and wondered how I would be able to go about this. Luckily, Learn provided very clear instructions on what to do as well as an hour-long video tutorial and with that, I got started.

I initially spent a good amount of time watching the video and googling around to familiarize myself with the terminology and the gem building process. Then I decided on the topic, the idea of which came pretty quickly to me. These days, I don’t have as much time to watch TV as I’d like but I thought it would be fun to learn about the top shows that are currently airing. I wanted to build a CLI that would scrape a variety of genres and enable the user to sort of filter and find out about shows according to their preferences/interests. I chose the Rotten Tomatoes website as my data source since it was pretty well structured, with data that was updated on a daily basis and would enable the gem to print out new information constantly. 

I worked out some ideas on paper for how the interface might look like as well as potential objects. The main thing that the assignment guidelines emphasized was to create a collection of objects, so I decided on genre/heading, show, and scraper objects in addition to the cli. I wasn’t exactly sure how the heading and show relationship would work, and struggled with trying to set up a show belongs-to headings relation. After some trial and error, I decided to keep the heading and show relation separate as this method was the first to work successfully. I’m planning to brush up more on collaborating objects and try to get the two to relate better in a future iteration since I feel like a belongs-to relationship here would be ideal. 

Towards the end, I was also having trouble with the CLI object as it was printing out extra sets of headings when the user returns back to the main menu. It took a while before I realized it was because my original array of headings was not being cleared after one iteration of the program. I needed to somehow clear the array or start a new one each time before starting the program over. I called the .clear method on the array, which fixed the issue.

I am pretty happy with how the CLI is working right now.  There are a few features that I think would be cool to implement, like maybe showing information about other seasons, actors, and reviews. Overall, I learned so much from doing this project. There was some frustration along the way, but it was really fun to see it all come together and slowly evolve into something that I had only imagined in the beginning. 
