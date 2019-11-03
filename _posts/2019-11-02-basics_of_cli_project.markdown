---
layout: post
title:      "Basics of CLI Project"
date:       2019-11-02 20:34:08 -0400
permalink:  basics_of_cli_project
---


Hi there,

In this post, I will write about the main concepts and tools I used to build my CLI Project. There are a variety of principles you have to implement in your project to make it work, but I will focus on the most important of them.

**Creating a GEM**
Gem is a universal, standard format of structure for programs and libraries. It comes as a package, and once you install it you dont need to worry about creating a respiratory and establishing dependencies between files - Ruby will do it for you!
You can install a gem using a bundler, simply type *bundle gem "name of your gem"* in your terminal.
Now your gem is created! one of the most important files in any gem is *gemspec* file that establishes dependencies for librarys development- it describes how all files are related and if you want to add additional dependencies (such as pry, nokogiri etc.) you can add them to this file as well. 

**Data Scraping**
Scraping is a process of transferring data from one source to your program so you can use that data in the way you decided. For this purposes, you can install Nokogiri (you install this bundler by requiring it in your gemspec file). In your lib file, you will describe the way how nokogiri is going to scape data from the source into your program. You will have to create a Class , and within this class define a method that will establish a variable (doc) equal to HTML of the source. 

**Class and instance variable**
Class is a block of different objects, operated through the methods. Since all methods withing the blocks are related, we often need to use variables outside the method, but within the class. In this case, we need to establish an instance variable by typing @ sign in front of it (@doc). 

**Class and instance methods**

Class might include two types of methods - class methods and instance methods. Class methods are used to operate the entire class of objects. Instance methods are encapsulated into the class and are used to operate objects within that encapsulated method only.

**CLI File**
CLI file of your code establishes the process of how the user will be interacting with the application. It also relies on creating a Class and different methods withing that class that are determining the output the user will see on the screen. 
If you want a user to answer the question, you need to make sure you have *input = gets.strip* after the question. It will give a command for your program to wait till the user responds. 

**Object instantiation**
When you create a new instance of the class,  you instantiate that object. In simple words, you create a concrete object and pass all arguments from those new objects to your initialize method. To do so, first, you need to define an initialize method within the class. Example: if you have created a class called *Cars*, you can create a method *initialize(brand)* within this class. You can later call *Cars.new("Toyota")* and it will create a new instance of the class *Cars*  called "*Toyota*". "String "*Toyota*" then will be assigned to a local variable *brand*. 

**Self word**
Self is a special variable (or keyword) that points out what exact object "owns" the code. 
Whenever you want to access the current object, for example, a Class, you can simply type self and Ruby will understand that the following code should be executed .E.g. : if self word is used in instance method, it refers to the instance of the class. If it is used in the Class method - it refers to the Class itself and will pass the message to the Class.

**Method Return Types**
There are two types of returns: explicit return and implicit. The keyword for explicit return is *return*. The unique characteristic of this type of return is that it has no return value (returns nil) and only return the argument itself. Therefore if there is no argument passed, it will return nil. Another characteristic is that once the method hits return keyword it stops executing any other commands after. Implicit return occurs when no return command has been called. In this case, Ruby will return the value of the last line evaluated statement in the body. 

**Iterating**
Iterating allows us to execute code over each element of an array separately, one-by-one. You can use *each* method to do so. 

The above are the basic concepts that helped me to build my CLI Project. 

Cheers,
Alina
