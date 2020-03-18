---
layout: post
title:      "Class Methods in Associations"
date:       2020-03-18 23:50:56 +0000
permalink:  class_methods_in_associations
---


Hi Everyone,

A few days ago I had an assessment for my Rails project. During the assessment, I was asked to refactor my code and make my users be able to view only the reviews they created. My users supposed to have many reviews. 
I was trying to figure out the best way to write a method, but all I thought was multiple line codes included a conditional statement. It did seem too complicated and I had the gut feeling that there should be a simplier way to complete a task. However, I spend 20 minutes trying to write code without any luck. Then my assessor kindly led me to the world of class methods. Apparently, there was a short one-line method to do what I wanted. It could be done so easily by calling a method directly on my association! Let me go through it.

What is the class method? 

A class method is a method that resides at the class level. It means that it is available to the entire class and can be used within it. In my case I had two classes:` User` and `Reviews`, so when I have a class method I can call it on any of my classes.

What is the Association?

Association in Rails is a relationship between classes. Classes might be `belong_to`, `has_many`, `has_one`, `has_many` through etc. In my case, a User` has_many Reviews`. 

How you can use it?

What I wanted to do is to simply show all reviews by a particular user. I did it through the following steps:

1) Since i already had a class User, I created a helper method called current_user. This method was using a class User that is identified by a current session.
2) I created a method Create for reviews that allowed to associate all reviews with the current_users (in other words the users that created them). 
3) Now I could call current_user.reviews on my "my reviews" method that allowed to show all reviews created by the current user. Simple as that! 

What other things you could do thanks to class methods?

I found the following methods useful:

collection.clear -E.g. current_user.reviews.clear - will delete all the reviews by a current user. 
collection<<(object, …) - E.g. current_user.reviews<<(review) will add a new review to the reviews of the current user
collection.size - E.g. current_user.reviews.size - will return a total amount of reviews by the ucrrent user. 

There are many other methods available and it definitely makes your life much easier. There is no need to complicate a code when you can get what you want with just a one-line method. 

Cheers,
Alina



