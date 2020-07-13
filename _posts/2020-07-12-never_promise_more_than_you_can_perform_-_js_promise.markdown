---
layout: post
title:      "'Never Promise More Than You Can Perform' - JS Promise"
date:       2020-07-13 03:47:46 +0000
permalink:  never_promise_more_than_you_can_perform_-_js_promise
---


When started learning about fetch requests, I have not realized what the heck promise is. I did understand that the fetch request is returning a promise and it is async, but I could never wrap my head around it. So in this article, I would like to go step by step through async requests and promises to have a crystal clear understanding of this important part of JavaScript.

**What is synch/async?**
The synchronous process is a one-step-at-a-time process. B will start only after A is done. Imagine you are a child who wants to watch TV. Unfortunately, your parents told you that you first have to finish your homework, and only then watch a TV. This case will be synchronous. You will watch TV after you finished your homework. 
Now imagine you are a teenager whose parents left you alone for a week. You can do homework and watch TV at the same time! Hooray! Now you can be asynchronous - you can do two things at a time. 

**How does JavaScript operate?**

JavaScript is a single-threaded language. In other words, it is synchronous. It can only process one statement at a time. First, it finishes processing one task, and only then it will start working on the second task. After the second task is completed, it will work on the third task, etc. However, it is not always convenient and efficient to have JS perform one task at a time. 
Imagine the following. You are making a holiday dinner. You need to make a soup, prepare a salad and make a cake. Soup can be made in 1 hour, a cake- in 2 hours and salad in 20 minutes. If you will prepare a dinner synchronously, one by one, it will take you 3 hours 20 minutes. But you can be more efficient and prepare dinner in 2 hours if you work asynchronously. You can prepare a cake and put it in the oven to bake for 1.5 hours. Then you can prepare ingredients for a soup and put it on the stove to cook for an hour. While the cake and soup are cooking, you can make a salad. After two hours you have three dishes ready for dinner!
While JS is a synchronous language, it has some async functionality-callbacks, async/await, and promises. 
It is always convenient when we have a long-long task and we have no idea if the result is successful or not. It will be very disappointing to wait until JS finished performing all tasks to hear back that the result is broken/unsuccessful. It would be cool if we can know right away if the task can be performed successfully or not. If yes. we can patiently wait. If not, we will know right away.

**When JavaScript perform tasks asynchronously?**
The most common use of the asynchronous model is fetch() request which is used to have front-end communication with your API. 
Calling fetch always returns a promise either fulfilled or rejected. After the promise is returned, it is considered to be settled. 
If it was returned fulfilled, then the chained method .then will be used to perform certain tasks with the returned data (such as convert it to JSON and send it to a reducer, etc. 
However, if a promise is returned as rejected, then JS will not even try to perform any tasks we wanted to perform it with the returned data.  
It is important to note, that the settled promise is immutable, so once it is either rejected or fulfilled it will not change. In other words, the promise can be called only once by fetch. 

**Why is the async model of fetch() is useful?**
When sending a fetch() request, we receive back a promise, either fulfilled or rejected. If during resolving it will be rejected, we will know about it right away. Imagine if you are baking a cake. If you put the too high temperature in the oven,  it will likely burn, and you will not have to wait for 1.5 hours to figure out that the cake is burnt- you will smell it pretty quickly. The same in fetch request. If at any point when JS tries to resolve the promise, it is rejected, then you will find out right away. For this purpose, you can set up a catch method to throw you an error occurring during the execution of the request.
Another important feature of async fetch response is that we use fetch() to get some data from our API. It might take a while until all data is downloaded from API. If fetch was async, it would mean that JS will stop executing all other processes and just focus on downloading the data. Meanwhile, all the user interface, all your front-end will be "blocked" waiting while JS finishes the task. It will negatively impact the user experience. However, with the async model, JS continues to perform other tasks (such as displaying user interface), while downloading data. Therefore the user will not notice that the data is still loading and no lags in-app performance will occur. 

**Conclusion** 
Asynch model is very useful for performance purposes when a large volume of data is loading or other complicated tasks are performed. It allows JS to keep performing other tasks while working on this big task, so it works efficiently and unnoticeably for a user. 


