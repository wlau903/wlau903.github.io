---
layout: post
title:      "JavaScript - Scope, Hoisting, Context, ES6 "
date:       2018-09-21 22:45:39 +0000
permalink:  javascript_-_scope_hoisting_context_es6
---


In this blog post, we will discuss a few main principles of JavaScript such as scope, hoisting and context. We will also look briefly at ES6 syntax and talk about how it relates to these topics. So let’s get started. 

**Scope & Context**

What is scope? Scope has to do with where something is in relation to other code. Where something is, and based on that location, what that something has access to. In terms of JavaScript, this means where declared variables and functions are visible. 

Scope can be thought of as being similar to a Slack channel. Only those who are members of a particular channel can view all the messages in that channel. People who aren’t members or those who haven’t been granted access to a channel can’t view those messages since they are not essentially “scoped” to that channel. Let’s now talk about execution context.  

All JavaScript code is run in what’s called an execution context, similar to how after you write a message in Slack, it will be sent through a channel. When we start off with a new JavaScript file, you are automatically inside an execution context called the global execution context. This initial context environment is what implicitly wraps all other JavaScript code that the file might contain.  Any variable or function that you declare here (provided that it's not inside a function or block) would also be considered as being in the global scope. Now when you are inside a particular context, you can write a method that references the variables and functions declared in that same context. Going back to our Slack example, when you’re inside a channel, you could write a message that references other messages in that same channel (as they’re all in the same execution context, you could say).  

Let’s go back to that new JS file from before.  It’s currently blank, so let’s fill it out. Here’s an example: 
```
function firstFunc() {
  return 92; 
}
// => undefined

const firstVar = firstFunc() * 10;
// => undefined

firstVar;
// => 920
```

Here, the `firstVar` is able to refer to and invoke `firstFunc()` because they are both in the same scope, the global scope. Variables and functions declared in the global scope can be referred to and called by any other piece of code in the file. Let’s take a look at another example: 
```
function firstFunc() {
  const firstVar = 92; 
}
// => undefined

firstVar;
// Uncaught ReferenceError: firstVar is not defined
```

We’ve declared a variable inside  `firstFunc()`, but when we tried to access the variable, we get an `Uncaught ReferenceError`. When we declared `firstFunc()`, we were in the global scope. However, once we’re inside the function body and declare `firstVar`, we are now in a new execution context along with its new scope. If we try to reference anything declared inside of that function while outside of that scope, we would get an error message. Here, we got the error because we’re trying to refer to `firstVar` which is in a scope that we don’t have access to. 

Now would be a good time to talk about the `this` keyword. `this` could be referring to one of a few different options, but it is really based on where it is located. If we’re inside an object’s method call, then `this` is equal to that object receiving the method call. If we are outside of a function, then `this` would be referring to the global object or the browser window. If we’re calling a regular function, `this` is set to the context that the function is in. Usually it would be the global object or undefined. With ES6’s arrow functions, `this` is equal to whatever the enclosing scope is, rather than having its own value. 


**Hoisting**

Now, let’s talk about hoisting. You may have heard of the different stages that the JS engine goes through while in the browser. In case you haven’t, we’ll do a quick refresher. So, the engine goes through two stages in the browser. The first stage is known as the compilation phase, where the engine scans through all of the code in your file, picks up any variable and function declarations, and sets some space aside in memory for those declarations.  For function declarations, the engine also creates a new execution context with a new scope as well as creating a reference to outer environment (or parent scope) to the scope chain. The second stage is called the execution phase. This is when the engine goes back to the beginning of the file but this time around, it will run through all of the code along with the previous declarations. 

Hoisting refers to how variable and function declarations are, in a sense, raised to the top of the file as the engine makes its first pass through the code. This is in reference back to the compilation phase where the JS engine first saves a reference to all variable and function declarations. Because of this initial collection of declarations, it can seem as though they are “hoisted” to the top of the file, when there is really no change in terms of physical location. 

There are a couple main ways to go about this in order to avoid confusion. One is to always put function declarations at the top of their scope, whether that may be the global scope or at the top of the function body. Another has to do with using ES6 syntax, which we’ll cover next. 

**ES6**

When ES6 was released, it also provided a couple new keywords for declaring variables. We can declare variables using the `var` keyword, and now we can also use `let` and `const` keywords. However, not all of them work the same way and in most cases, we’re better off sticking to `let` and `const`. Consider this example: 
```
var newVar = 26;
// => undefined

var newVar = 27;
// => undefined

newVar;
// => 27
```
Here, we’re able to declare a variable twice without an error being thrown. This is not ideal since there is no reason why we should be declaring variables twice. 
```
let newVar = 26;
// => undefined

let newVar = 27;
// => Uncaught SyntaxError: Identifier 'newVar' has already been declared
```
Using `let` and `const` keywords will help to keep ourselves in check, as shown above. `const` is an even safer option as variables declared with `const` cannot be reassigned. The difference here is that with `let` and `var`, we can reassign the values but variables declared with `const` cannot be reassigned. 

`var` has some other weirdness when it comes to scope. Variables declared with `var` are not block-scoped, in that they can still be referenced outside of the block that they were initially defined in. 
```
if (true) {
 var newVar = 80;
}
// => undefined

newVar;
// => 80
```

However, variables declared with `const` or `let` ARE scoped to the block and cannot be referenced outside of it. 
```
if (true) {
 const newVar = 80;
 let anotherVar = 5;
 }
 // => undefined
 
newVar;
 // => Uncaught ReferenceError: newVar is not defined 
 
 anotherVar;
 // => Uncaught ReferenceError: anotherVar is not defined
```

How does ES6 syntax relate to hoisting, as previously mentioned earlier? Well, using `var` has another quirk involved where the keyword allows the JS engine to reference a declared variable even if it hasn’t been initialized. In order to avoid issues with `var`-related hoisting, your best option is to use either `let` or `const` to declare variables. Because even though their declarations will be hoisted, the JS engine will not allow them to be referenced before they’ve been assigned a value.

That's all we've got for this post! If I've made any errors or if you have any other questions, please don't hesitate to reach out. Happy coding everyone :)
