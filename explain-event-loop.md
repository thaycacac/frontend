# Explain Event Loop 

JavaScript is a single-threaded programming language. This means that JavaScript can do only one thing at a single point in time.

Inside Browser, there is a Javascript engine (we are considering V8 for chrome.) and an environment to run javascript properly. Javascript engine has two parts, **Heap** and **Call Stack**. And the engine has some assistant named Web APIs and Callback Queue.

## Heaps

It's an unstructured memory block. Our code's memory allocation happens here. As a programmer we don't have to worry much about heaps.

## Call Stack

We can consider Call Stack as a kitchen where all our code executed or cooked. Whenever we try to run a piece of code, it goes to call stack first and then executed. It works in LIFO style. That is Last In First Out.

## Web APIs

Web API works as JS engines assistant. When JS engine have to deal with asynchronous code, it takes the help of Web API. Web API handles the blocking behavior of JavaScript code.

## Callback Queue

It's a guard who monitors the stack of asynchronous callback functions who just completed the task of waiting and passed the gate of Web API. Callback Queue works using FIFO (First In First Out ) method. And now, they waits here to go back to Call Stack.

## Event loop

Event loop is just a guardian who keeps a good communication with Call Stack and Callback Queue. It checks if the call stack is free, then lets know the callback queue. Then Callback queue passes the callback function to Call stack to be executed. When all the callback functions are executed, the call stack is out and global execution context is free.

The following picture illustrates JavaScript runtime, Web API, Call stack, and Event loop:

![image](https://user-images.githubusercontent.com/29374426/183848825-fe73d872-8bd6-478d-a9d2-480acd30188e.png)
