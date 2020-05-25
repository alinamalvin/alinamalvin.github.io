---
layout: post
title:      "Hoisting in JavaScript: step-by-step explanation"
date:       2020-05-24 22:22:36 -0400
permalink:  hoisting_in_javascript_beginners_guide
---


To understand what hoisting in JavaScript is, let first refer to a definition of this word:
*Hoist - raise (something) by means of ropes and pulleys* (Merriam-Webster Dictionary)
This term is often used in terms of raising a flag, for example:
> Pirates hoisted a black flag approaching to their enemies land as a signal they are going to attack
![](http://25.media.tumblr.com/28ba63e1c73b4d4820942c2ab8b611af/tumblr_mib3kwCeub1s0mb6co1_500.gif)

Therefore, hoisting as a noun can be defined as an act of raising something. While hoisting in JavaScript gives its hoisting much more amicable meaning than pirates, it’s intention is still the same - to declare an act before it’s execution.

**Variable Hoisting** 
**Var**
In programming, we use variables. variable is a value that can change, depending on conditions or on information passed to the program. Let’s take an example using the analogy with pirates. 
Imagine, we decided to build a Pirates Attack game app. There are two players-one plays for pirates, and another one - for defendants. We approached the part in our code, where we need to make sure pirates have their flags on the ship when they are leaving their land to enemies' land to raise it. We do not know yet what color of the flag pirates will raise (it depends on the second player’s actions). While approaching the enemiies land, the captain may look at the binocular and sees that the land is full of gold, then he will give an order to raise a black flag. Otherwise, he might look at the land and see that there is his old buddy from elementary school is living there, and he doesn’t want to attack him, then he will give an order to raise a white flag. All we care for now is that pirates ship need a flag variable in our app sometimes in the future, and we can determine the value later.  
![](https://a.radikal.ru/a04/2005/c3/dbd308015243.pnghttp://)

In JavaScript language, this act is called *variable declaration*. We declared a variable, but we haven’t assigned it yet. 

Let’s come back to our pirates. The Captain has looked into the binocular and saw that everything is made out of gold in the enemies’ land. He decides to invade the enemy. He gives to raise a black flag on the ship, in other words he assigns a black flag to be raised. You, on your end as a programmer, need to assign a var flag to be a black one.  
![](https://c.radikal.ru/c02/2005/a6/3ab889faa4a7.pnghttp://)

The next thing to do is to raise this black flag on the ship. You, as a programmer, need to have a method called raiseFlag() where you will pass flag as an argument.  
![](https://c.radikal.ru/c06/2005/ad/d64a9c682e05.png)

Let’s see the steps we took to use our variable:

1.  We declared the variable `flag`
2.  We assigned the value `"blackFlag"` to our variable 
3.  We executed the variable in our `raiseFlag()` function.

What would happen if we change the order of our commands? Let’s say the captain told to bring a flag on the ship without specifying which one, and then, after looking in the binocular, he gives a command to raise a flag. What flag will be raised? Let’s see.
 
Oops! `Flag` is `undefined`.
![](https://c.radikal.ru/c19/2005/c1/6dc6d80acd0f.png)

Now let’s imagine that the captain is getting old and forgot not only to tell what flag to raise, but he forgot to tell the crew to bring the flag on the ship at all! 
![](https://d.radikal.ru/d01/2005/30/bd465fc0b021.png)

`Flag` is `undefined` again. However in the case above we haven’t run into the error due to us trying to execute the undeclared variable. The code was still running, it just gives us an undesired result - the variable is undefined. This is exactly what hoisting does! JavaScript has hoisted (invisibly to us, behind the scene) the variable declaration above the rest of the code. In other words, due to hoisting, JavaScripts can identify the variable declaration first, and runs the rest of the code. From JavaScript ’s point of view, there is no difference between the last two snippets of code -  it sees it as shown on the first snippet. 
Due to this reason, we have to be careful and always declare and assign the variable simultaneously: 
![](https://a.radikal.ru/a22/2005/a3/47f2833eb2f6.png)

**Let** 
The variables declared with `var` keyword are function scoped (they can be seen throughout the entire function). Now let’s examine what happens when we use block-scoped variables defined with `let` and `const` keywords.  
![](http://a.radikal.ru/a14/2005/bd/853111c3be47.png)

If we try to call a `let `variable before we declared and initialized it, we do not get undefined anymore, but we see a `Reference Error: variable is not defined`. It means, that our code can no longer be executed before the variable is declared. And the reason that it cannot be executed, is that JavaScript can no longer initialize the variable behind the scene to run the following code.
Now, let’s try to declare a variable before the execution code, and assign it after.  
![](http://d.radikal.ru/d11/2005/da/cdb560a9a439.png)

Wohoo! JavaScript will still run the code even if the variable was not assigned yet, and gives us `undefined`. However, such implementation will most likely cause an undesired outcome when you run your application. And again, we come to the importance of declaring and assigning variables before executing them.

**Const**
There is one more keyword that ES6 has event a stricter mode for - `const` . It is, similar to `let` variables, is a block-scoped variable, but it has its differences. Unlike `let` variable, `const` is immutable variable, which means it cannot be reassigned to a different value. If `let` allows code to be executed when the variable was at least declared before the execution, `const` will not execute code at all unless a variable was both declared and assigned prior to execution.  
![](http://c.radikal.ru/c34/2005/16/1c34e835175a.png)

Even if it was declared before execution, but no assigned, the result will be still the same (error): 
![](http://a.radikal.ru/a22/2005/6f/583f09815afe.png)

ES6 still performs hoisting in all cases considered above: `var`, `let`, and `cosnt`. It means that it is still scanning behind the scene to find the declared variable and raise it to the top or above the execution code. But the difference is in initialization (or assignment) outcomes: 
`Var` is initialized with a value “undefined"
`Let` and const remains initialized (just declared)

**Hoisting functions**
All functions can be divided into two types: Function Declaration and Function Expressions

**Function Declarations**
Function declarations, similar to variable declarations, are hoisted. We can call a function before declaring it.  
![](http://a.radikal.ru/a19/2005/7f/00fd271addbe.png)

**Function Expression **

Function Expressions are not hoisted. Let’s try:
![](http://b.radikal.ru/b35/2005/95/5aec50f237a6.png)
 
Even if we try to declare a function and express it, JavaScript will only hoist the declaration, but not the assignment. Therefore, it will not see that variable as a function:
![](http://c.radikal.ru/c30/2005/e6/ac220c0de162.png)

**Precedence:**
Hoisting also has a specific hierarchy:
![](http://c.radikal.ru/c22/2005/e3/d153f5b47112.jpg)

When hoisting, JavaScript will always make a priority to hoist variable assignment over function declaration, and a function declaration over the variable declaration.
![](http://d.radikal.ru/d08/2005/e1/b9ccc28cd962.png)

As we see, JavaScript applied the assignment to the “flag” given by it’s variable, not the function declaration. But if we just declare a variable, then JS will prefer hoisting function declaration instead:
![](http://d.radikal.ru/d40/2005/60/a2b2c57be869.png)

**Classes**
Classes, similar to functions, can be classified as declaration classes and expression classes. 
Declaration class is hoisted, but remains uninitialized:
![](http://c.radikal.ru/c10/2005/d1/b61defe91065.png)
 
We get a Reference Error that the flag is not defined, which means that though variable declaration BlackFlack was hoisted, it stayed uninitialized because JS didn’t find what Flag is. But once we reverse the order and declare the class variable Flag first, JS can successfully identify the class Flag and use it.
![](http://a.radikal.ru/a20/2005/31/5617363dba78.png)

Class expressions, same as function expressions, are not hoisted:
![](http://a.radikal.ru/a43/2005/70/205833707f31.png)

JS did hoist var Flag, but as a variable declaration (remember the hoisting priority of arable declaration over function declaration?), not as a function. Therefore, it didn not hoist the variables assigned to a class.

Conclusion
To summarize all the above, lets bring all the information into a diagram:
![](http://c.radikal.ru/c14/2005/f2/b1e39176ce13.jpg)
