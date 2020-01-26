---
layout: post
title:      "Planning your first Sinatra app"
date:       2020-01-26 17:19:49 +0000
permalink:  planning_your_first_sinatra_app
---


My today`s post will be about how to plan your Sinatra project. Planning involves a few steps:
1) Plan what you want to write your app about. 
    I truly believe that the first project you write should be about the thing that makes you excited and you yourself would use this app. Why? Planning to use this app yourself gives you an opportunity to view it as a user, not a developer. Then you will be able to figure out what useful features are missing and improve the app. And why do you need to be excited? Well, excitement will drive you to make an excellent product and not to settle on less!
        
        E.g.: I built my app that allows users to track restaurants they visited. I chose it because I eat out a lot and always forget the names of the places I went to. So this app will allow me to see all the places I`ve been to.
    
2) Write down what do you want users to be able to do on the app.
 Just a simple list of what users can do on your website will help you to get a clear understanding of what models to build.
  
    E.g. I wanted the users to be able to add and view restaurants they have been to, and view restaurants other people visited as well. Also, users should be able to edit and delete restaurants they added.
 
 3) Creating an association model. 
   You have to have a clear understanding of how different models and data will be related to each other. Will a user have many items? Or will an item has many users? I think it is one of the most important steps because the incorrect association will cause a lot of bugs later that might be hard to fix without deleting your database and starting from scratch. I suggest spending enough time building a diagram that gives you a visual understanding of how items and users are related within your app.
     
>      E.g. Originally I set up my association in the way that a user has_many restaurants and restaurants has_many users. However, it made be unable later to make sure only users who created the restaurants can edit/delete it. I had to delete the database and set up a new one, where user has_many restaurants and restaurant belong_to user. 
>      

Tha`s it! Your planning is complete and you can start creating your database and building models and controllers.

Hope this information can be useful and good luck on your Sinatra project!

Alina
