---
layout: post
title:      "Global state with Redux"
date:       2020-07-23 16:45:30 +0000
permalink:  global_state_with_redux
---


Hi friends! I recently finished working on my app built with JavascScript using React/Redux and I feel that it will be good to write a blog with a focus on one of the most useful front-end libraries - Redux. 

Why Redux library is useful?

Imagine you built a React front-end with many components, and half of them are class components (which have states). You have to always remember to pass state as props from one component to another, and once the app becomes bigger it gets complicated. Also, if you would like to make a change in the state, you will have to make changes in every single container that has these props. Would not it be easier if there is one global place where the state is stored? And this place does exist- it is called Redux! 
Redux creates a store that is centralized and persistent. All states are now stored safely in one place. They are retrieved from the store by components and, once updated, pushed back to the store. It also allows you to better organize your app based on whether or not the components are connected to the store (presentational vs container components).

How Store and Components are connected? 

In order to connect a component to the store two elements need to be implemented:
1) Redux needs to be imported from 'react-redux'
2) The `connect()` function needs to pass certain functions as arguments from the store to the component: 

![](https://c.radikal.ru/c32/2007/18/80987afcbf23.png)

The 2 functions we need to pass are mapStateToProps and mapDispatchToProps. Let's talk about each of them.

mapStateToProps

This function does exactly what is says - it retrieves the state from the store and brings it to Component as a prop. We can compare it to a "Subscribe" button - once the function is passed into connect() method, the Component "subscribes" to get updates from the redux store. It means, that the function is triggered every time the state is updated in the store. So, every time the state is updated in the store, the component is re-rendered right with an updated state. 
We need mapStaeToProps to GET the data from the store. 
This function is the only one required to be passed as an argument to connect() function. Therefore, if your component does not need to obtain any states from the store, then you have to put null as a first argument. 

Because the main purpose of mapStateToProps function is to pass the state from the store into the component, we need to pass the state (obtained from the store) as an argument for this function. It will look like this:

![](https://b.radikal.ru/b30/2007/53/a0f64376fc02.png)

The code below retrieves the state from the global store to Component via connect() function. It then passes this state (our state has a key `items`) as an argument to mapStateToProps function. The later returns an object, where it sets the Components state equals to the state returned from the global store. In other words, mapStateToProps is a function that provides the store data to your component.

mapDispatchToProps

By analogy to the previous function, we can guess that mapDispatchToProps retrieves the dispatch method from the store and brings it to Component as a prop. This function provides your Component with action creator (which is represented by the `dispatch()` function. When mapStateToProps function supplied our Component with the state, it needed to pass this state as an argument. In the same manner, mapDispatchToProps needs to pass the dispatch function as an argument. It is how it delivers the action creator to the Component. Dispatch function then passes an actual action as an argument to specify what exact action needs to be performed in order to update a state. 
We need mapDispatchToProps to UPDATE the data in the store. 

![](http://a.radikal.ru/a05/2007/f4/eac6cc1dbed5.png)

But this is not enough to make changes to the global state. We also need to write a function that is triggered by the event that supposed to change the state (for example clicking on a Submit button):

![](https://a.radikal.ru/a18/2007/dc/c6b121528cfc.png)

In the snippet aboмe we initialize a function that returns an action creator function (that we have passed from the redux store. This action creator function grabs the new item we created from the component, pass it as an argument to the reducer via dispatch() function and add it to a global state via reducer:

[](http://c.radikal.ru/c39/2007/b9/a01a27befc25.png)

The dispatch() function (or mapDispatchToProps) is not required for connect() function. It can be omitted, and we still will have access to the actions. However in this case when we are trying to send our data to the reducer to update the state, we will need to write the entire dispatch function  `this.props.dispatch(addItem())`. When we have more than one action, it is better to write mapDispatchToProps function in order to keep all our actions organized and abstracted. However, you can keep in mind that dispatch() function is passed by connect() by default even when we have no passed it as a second argument and is available for your use in the Component. 

Conclusion

Here we can list the purposes of each of the functions described above:
connect() 
•Creatr container components;
•Subscribe this component to the redux store

mapStateToProps
•Subscribes a component to receive state updates from the store.
•Provides component with data that becomes components property.


mapDispatchToProps
•Used to enable the component to send state updates to the store. 
•Provides component with action creator function that becomes components property. 


The Redux is a great way to organize your components and their state. It is easy to use it because it is straightforward and, as e could see from the above, requires only 5 steps to make it work:
1) Import connect from react-redux
2) Write a connect function and pass 1-2 arguments depending on the task of the component.
3) Write mapStateToProps function
4) 4.1. Write mapDispatchToProps function 
    4.2. Write the Action Creator component.
    4.3. Write a Reducer
