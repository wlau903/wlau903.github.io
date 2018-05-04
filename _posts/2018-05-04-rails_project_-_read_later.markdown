---
layout: post
title:      "Rails Project - Read Later"
date:       2018-05-04 21:50:56 +0000
permalink:  rails_project_-_read_later
---


Third project, wow, here we go! Rails was the hardest unit for me so far in the Learn curriculum, due to a combination of various factors. Material wise, it wasn’t so much that the concepts were difficult this time around but it was just more instances of needing to look things up again. Life was also happening and with my going through bouts of low energy, I wasn’t coding as much as I’d have liked to on a daily basis. But all that aside, I’ve made it to the end and I’m feeling thankful and happy with what I’ve built. 

I wanted to make a web app that was similar to Pocket, and essentially mirrored my own project where users would be able to save articles to a reading list that they can access again at a later time.  The app is called Read Later, with article information scraped from the top headlines of each category and subcategory from The Guardian website. Users would be able to navigate through the articles freely, but are required to login if they wanted to save an article or create/view a reading list. 

My model associations: 

A User has_many Reading Lists,  and has_many Articles through Reading Lists
A Reading List belongs_to a User, and has_many Articles
An Article belongs_to a Category, belongs_to a Subcategory, and belongs_to a Reading List (default: optional)
A Category and Subcategory both has_many Articles

Overall, it was an incredible learning experience building out the app. I got more practice with scraping and analyzing CSS selectors. I ran into some difficulty while trying to configure Omniauth through Google, but eventually got things working thanks to the great community on Stack Overflow. Yes, there were a few times when I got overwhelmed and frustrated.  What really helped was taking a breather every so often (easier said than done!) and revisiting the issue while feeling refreshed. I can’t recommend this enough..that and with a positive attitude, you might just have a whole web app built by the end of it. :)
