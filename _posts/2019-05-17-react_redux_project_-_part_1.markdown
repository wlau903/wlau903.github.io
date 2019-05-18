---
layout: post
title:      "React Redux Project - Part 1"
date:       2019-05-18 03:35:38 +0000
permalink:  react_redux_project_-_part_1
---


I can’t believe that it’s now time for the final project of the Learn program. Truthfully, this project has been a long time coming for me. It’s been several months since I completed the last one what with life happening and balancing a part-time retail job along with going through the curriculum. But I’m so glad to be able to devote more time to coding now and gain back momentum!

So for the final project, I decided to build a Chinese restaurant ordering application. I wanted users to be able to view a menu, add menu items to a cart, as well as place orders that would later be ready for pickup. 

Before this project, I was still a little shaky in terms of my understanding of React and its various capabilities. It wasn’t until I watched a couple of Learn videos on how to set up a Rails/React app and went back over lessons in the curriculum that I began to feel more confident about how I would start and structure my project. 

Once I set up the app using create-react-app and got the menu items displaying from the backend, it was like a light then went off. I was starting to see how the different pieces would be connected to each other. I became more comfortable with passing data down through props from parent to child components. I then became really comfortable with managing my app state locally by means of React’s ’setState’, and changing the state through callback functions such as when adding and removing items from a cart, as well as going through the checkout process. 

There is also the option of keeping my app state globally through a Redux store. A benefit of using Redux is that it adds scalability to your app when getting ready for production. It also enables components in your app to extract specific pieces of the state from one central location, instead of having it be passed down from a parent component nor do surrounding components need to know about what data they’re accessing. However, using Redux can also make things a bit more complicated at times depending on the nature of the state or type of data. I plan to ask the Learn instructors and see what they recommend for my project. If I were to incorporate Redux into my app, I’d see it being useful for keeping newly-created orders in the store (seeing as the store will reset upon refresh and I want to display a confirmation message once an order has been placed). 

To be continued..
