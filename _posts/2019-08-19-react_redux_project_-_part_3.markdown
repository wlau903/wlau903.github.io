---
layout: post
title:      "React Redux Project - Part 3"
date:       2019-08-19 06:41:44 +0000
permalink:  react_redux_project_-_part_3
---


So picking up where I left off in my last post, I had mentioned creating a function called `getDishes()` inside the `actions/index.js` file. And what this function does is key to what we’ll be discussing for the rest of this post. 

The first thing to remember is that the way Redux updates the store is that it dispatches action objects that then call the reducer, which then modifies the state (or returns back the original state) based on the information contained in those actions. Now `getDishes()` is what is known as an action creator function, where it returns an action (otherwise known as a plain old JavaScript object) when invoked. The thing about actions in Redux is that by default, they are dispatched synchronously. However, this would be an issue if we want to make asynchronous calls to an external API or if we want to perform other side effects. But no worries! We can fix this by taking advantage of a middleware called Redux Thunk. What this middleware does is it enables action creator functions to return a function instead of an action object. That returned function will receive the store’s dispatch method as an argument, and this allows us to dispatch multiple (synchronous!!) actions within that returned function while also taking into account any asynchronous web requests and waiting for them to properly resolve.

I incorporated the Thunk middleware into my project by first installing the package by running `npm install --save redux-thunk` while in the root folder of the project directory. Then inside the `index.js` file where the store is created, I added in the middleware by using the `applyMiddleWare()` from Redux with thunk provided as an argument like so: 

`const store = createStore(rootReducer, composeEnhancers(applyMiddleware(thunk))); `

With these two steps completed, we’re now able to dispatch actions in our app that will coordinate appropriately with the asynchronous requests that we’ll be making to our backend API.
