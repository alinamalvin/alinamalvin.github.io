---
layout: post
title:      "Looping. As simple as it can be."
date:       2019-11-01 18:30:49 +0000
permalink:  looping_as_simple_as_it_can_be
---


In this post, I will try to explain Looping in the simplest way I can. To do so, I am going to relate coding to a thing that is very familiar to each of you-signing the postcards. 

**What is loop?**

It is finally Christmas time and you bought 20 Christmas cards. You bought 15 funny cards for your friends and 5 that were designed specifically for family members (mother, father, grandma, grandpa, and your sister). Now you must sign each card with your name. You did 3 cards and got tired. Wouldn’t it be cool if you could just sign one card and the rest of the cards will be signed automatically with the same signature? If you could do it, you will create a loop- a rule that is going to repeat itself as many times as you decide.

**How it works in programming?**

If you transform this into a programming language, you will have to write the following:


loop do
  puts "With Love, Alina"
end

This loop will be signing an unlimited number of cards. Since you only have 20 cards to sign, you want to set up the number of cards to sign. You can do this by setting up additional #break requirement:

i = 0
loop do
  i += 1
  puts i
  if i == 20
    break       
  end
end

Great! Now all 20 cards will be signed automatically!

**Why is it useful?**

It is one of the most important tools in programming because it allows automating the process

I hope it helped you to understand looping better!

Cheers,
Alina
