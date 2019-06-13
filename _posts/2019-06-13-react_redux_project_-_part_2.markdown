---
layout: post
title:      "React Redux Project - Part 2"
date:       2019-06-13 17:38:33 +0000
permalink:  react_redux_project_-_part_2
---


Hi all! Since I last blogged, I got some feedback on my final project and implemented a few changes. Initially, the menu was being rendered in App component’s `componentDidMount()`, with the API call made via service worker and the menu data passed down and rendering through a presentational component. I needed to create an additional stateful/container component as well as add a Redux store and async actions to fulfill the project requirements so I decided to shift some things around and utilize Redux to help render the menu. 

I first integrated the Redux packages into the app and added in the Provider component from `react-redux` and the `createStore()` from `redux`.  Then, I created a stateful component that would be connected to the store and had it set to receive menu items from the store state through its props. I also added a presentational component that would be used by that stateful component to render each menu item in the browser. 

The next step to get the menu rendering was to create an actions directory and the `index.js` file, which would be called from a `store.dispatch()` call that I would later add into `src/index.js` file (before the app is first mounted onto the DOM). For this project, I decided to group all the actions I’d need into one single file but it’s also an option to have multiple action files. In that `index.js` file, I made a `getDishes()` where inside that function, there’d be a fetch call to the API for the menu data, and parsing of that data into json if we get a successful response back. Once the data is in the proper json format, we will then create an action object to be sent to the reducer with the response data attached as a payload. At this point, I then created a reducers directory and created a file (`dishesReducer.js`) to serve as the menu reducer. I defined a `dishesReducer()` which is essentially a switch case statement that looks at the type property of the action object that it would later receive.  If none of the case statements are met, the reducer would just return back whatever the state is at the start of the function call.

I followed this similar flow for migrating the create orders functionality to the Redux store with the exception of calling the store’s dispatch method from a component rather than how I had done earlier and called it from `src/index.js` file. We can also make calls to dispatch actions from any other component in our app if we wish. The ability to do this is another benefit of using Redux and how by wrapping the Provider component around our main App component as we did earlier, enables us developers to be access the store from any other component regardless of where it sits on the component tree (parent vs children components, etc). 

In my next post, I’ll walk through how I implemented Redux async actions using Thunk middleware. Stay tuned! 
