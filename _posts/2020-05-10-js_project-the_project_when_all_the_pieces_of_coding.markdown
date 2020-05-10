---
layout: post
title:      "JS Project-the project, when all the pieces of coding "
date:       2020-05-10 21:34:46 +0000
permalink:  js_project-the_project_when_all_the_pieces_of_coding
---

Hi there! 

I finished my JS project yesterday, and, with no doubts, I can say it was the most difficult project so far. I certainly was much more confident while working on the backend part (thanks to previous experience on Rails project!), but JS frontend- it is what made me sweat!

!Me sweating on JS[](https://media.giphy.com/media/3oKHWspJ9dRB1DSQIE/giphy.gifhttp://)

However, the deeper then previously understanding of backend functionality helped to move to avoid many mistakes and solve errors pretty fast! Wooh!

My app is for travelers who quickly need to create a packing list for their trip. They simply can choose a trip style and the app will create a list of items necessary to pack. Users can also add new items to the list or remove an existing item. 

My app is based on two models - `Trip` and` Item`. Each `Item belongs_to Trip`, and a `Trip has_many Items`. Therefore, when `Item` is created, it is assigned to `Trip` via `trip_id`. The trips database is fixed, meaning the user shouldnt be able to modify existing trips. However, the items database has a more dynamic approach. It has three of CRUD functionalities - create, read, and delete. 

To read all items that belong to the trip a user has to choose a trip style and click the button "Generate a Packing List". Once the button is clicked, the eventListener calls a function `createCutstomizedItems,` that is responsible for filtering all the existing items by the chosen `Trip` name. Once all the trips are filtered, it creates a node in DOM, inserts items name as innerText HTML to this node, and also adds a delete button next to each of the items. Then it is rendering all the items for a user to view. If a user chooses to delete an item, he can click the `Delete` button and an item will immediately disappear from the list. If a user wants to add an item, he can fill out the `Create New Item` field, choose a trip that his item should belong to, and click the button `Submit.` Once the new items are submitted, it is immediately shown in the packing list. 

One of the problems I faced with this project was that my event listener for the delete button did not  work when I had a special method for it. I had to figure out that the `eventListener` has to belong to the existing button, not the potential one. Because my packing list was created only after a user clicked on the "Generate a Packing List" button, it was necessary to insert the function with `eventListener` into `createPackingList` method, as this button only existed within packing list. 

Another problem was that when the delete method deleted an item from the database, it still was showing up on the existing list. The problem was that the actual DOM node was not removed, but adding a `remove()` method solved the problem. 

Overall, the project was fun and very dynamic, though it was challenging enough to teach a variety of new skills. I found a better approach for problem-solving (using debugger,` console(log)` and Dev console), and started to distinguish the root of the problem between backend and frontend. 


