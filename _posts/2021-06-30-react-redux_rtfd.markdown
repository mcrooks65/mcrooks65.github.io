---
layout: post
title:      "React-Redux RTFD"
date:       2021-06-30 19:25:33 -0400
permalink:  react-redux_rtfd
---


It's come to my attention that even though i've managed to put together my entire final project, my understanding of the intricacies of the React-Redux framework is still lacking.  This blog entry is my attempt to demystify this framework by breaking down it's most key components as explicitly as possible.  In no particular order i will go through each concept as  thoroughly as I can manage.  I will make heavy use of the official documentation and quote it where neccessary but also will relate each concept to my projec where applicable and offer  

**1) Create Store**

***The Redux Store***

Brings together the state, actions, and reducers that make up your app. The store has several responsibilities:

-Holds the current application state inside

-Allows access to the current state via store.getState();

-Allows state to be updated via store.dispatch(action);

-Registers listener callbacks via store.subscribe(listener);

-Handles unregistering of listeners via the unsubscribe function returned by store.subscribe(listener). 

***createStore(reducer, [preloadedState], [enhancer])***

Creates a Redux store that holds the complete state tree of your app. There should only be a single store in your app.

*Arguments*

*-reducer (Function)*: A reducing function that returns the next state tree, given the current state tree and an action to handle.

*-[preloadedState] (any*): The initial state. You may optionally specify it to hydrate the state from the server in universal apps, or to restore a previously serialized user session. If you produced reducer with combineReducers, this must be a plain object with the same shape as the keys passed to it. Otherwise, you are free to pass anything that your reducer can understand.

*-[enhancer] (Function*): The store enhancer. You may optionally specify it to enhance the store with third-party capabilities such as middleware, time travel, persistence, etc. The only store enhancer that ships with Redux is applyMiddleware().

*Take a look at the code from my project's index.js file: *
![React-Redux RTFD #1](https://i.imgur.com/deC4Bqj.png?1)

-Line 4:  **createStore** is imported from **'redux'** along with applyMiddleware and compose.

-Line 5: **thunk** is imported from a different library: **'redux-thunk'**

-Line 6: The **Provider** is imported from **'react-redux'** and is where your store must live.

-Line 14: Where the **createStore()** function is called, and in my case I used two arguments, a reducer and enhancer.  No need for a preloaded state as I hydrate the state from a backend rails server elsewhere.  Enhancements used are to get asyncronous access via 'thunk'.

-Line 17: Note that the **store** lives in the **Provider**, which is wrapped around the app, and also a router in this case.

**2) Reducers**

Reducers are functions that take the current state and an action as arguments, and return a new state result. In other words, (state, action) => newState.

*A few special rules regarding reducers*

-They should only calculate the new state value based on the state and action arguments

-They are not allowed to modify the existing state. Instead, they must make immutable updates, by copying the existing state and making changes to the copied values.

-They must not do any asynchronous logic or other "side effects" aka any change to state or behavior that can be seen outside of returning a value from a function

*The main reducer in my project:*
![React-Redux RTFD #2](https://i.imgur.com/JWrlynP.png?1)

-Line 1: Just as it was described above, the reducer function is declared as 'engagementReducer()' and it takes the two arguments, a state: which is initially set as an object with an empty array with key 'engagements', and an action: which will be defined more fully further down this list, but know that the action provides a 'type'.

-Line 3: This switch case handles what type of action is being passed to the reducer.  

-Lines 4,6,8,17, 26: All seperate examples of action types with their respective reducer return statements beneath.

**3) Dispatch**

The Redux store has a method called dispatch. The only way to update the state is to call store.dispatch() and pass in an action object. The store will run its reducer function and save the new state value inside, and we can call getState() to retrieve the updated value:

*(example from redux.js.org docs)*

store.dispatch({ type: 'counter/incremented' })

console.log(store.getState())

// {value: 1}

You can think of dispatching actions as "triggering an event" in the application. Something happened, and we want the store to know about it. Reducers act like event listeners, and when they hear an action they are interested in, they update the state in response.  Since we tend to call dispatch inside of actions i'll reserve a project screenshot for the next section.

**4) Actions**

Actions are plain JavaScript objects that have a type field. You can think of an action as an event that describes something that happened in the application

The type field should be a string that gives this action a descriptive name, like "todos/todoAdded". We usually write that type string like "domain/eventName", where the first part is the feature or category that this action belongs to, and the second part is the specific thing that happened.  Since my project is limited in scope I didn't bother making subcategories, but will keep it in mind for larger projects.

An action object can have other fields with additional information about what happened. By convention, we put that information in a field called *payload*.

*Here's example action from my project:*
![React-Redux RTFD #3](https://i.imgur.com/htLTSaX.png?1)

-Line 1: Declaring a constant addTarget that requires two arguments, a target and it's associated engagementId. 

-Line 3-9: This fetch function makes an POST request using the provided target in the argument as well as the engagmentId to find the proper path to the backend.

-Line 12: Our dispatch is called, and we pass in our action object, which contains a type: 'ADD_TARGET' and a payload: 'engagement' which is retrieved from the previous fetch requests by chaining .then's after.


**5) Connect**

The connect() function connects a React component to a Redux store.

It provides its connected component with the pieces of the data it needs from the store, and the functions it can use to dispatch actions to the store.

It does not modify the component class passed to it; instead, it returns a new, connected component class that wraps the component you passed in.

*connect accepts four different parameters, all optional. By convention, they are called:*

-mapStateToProps?: Function

-mapDispatchToProps?: Function | Object

-mergeProps?: Function

-options?: Object

*To specify the React component/container you're connecting to uses the following format:*

connect(mapStateToProps?, mapDispatchToProps?, mergeProps?, options?))(component/container)

**connect** is imported from **'react-redux'**

*Example from my project in next section since connect requires the use of MapStateToProps.*

**6) MapStateToProps**

If a mapStateToProps function is specified, the new wrapper component will subscribe to Redux store updates. This means that any time the store is updated, mapStateToProps will be called. The results of mapStateToProps must be a plain object, which will be merged into the wrapped component’s props. If you don't want to subscribe to store updates, pass null or undefined in place of mapStateToProps.

*Example from my project - Also shows connect() and how MapStateToProps fits in on Line 45*
![React-Redux RTFD #4](https://i.imgur.com/xpj51Wf.png?1)

**7) MapDispatchToProps**

Conventionally called mapDispatchToProps, this second parameter to connect() may either be an object, a function, or not supplied.

Your component will receive dispatch by default, i.e., when you do not supply a second parameter to connect():

// do not pass `mapDispatchToProps`

connect()(MyComponent)

connect(mapState)(MyComponent)

connect(mapState, null, mergeProps, options)(MyComponent)

If you define a mapDispatchToProps as a function, it will be called with a maximum of two parameters.  This isn't something I had to do in my project, so i'll use the examples from the react-redux.js.org docs.

*1) dispatch: Function*

If your mapDispatchToProps is declared as a function taking one parameter, it will be given the dispatch of your store.

![React-Redux Docs Example #1](https://i.imgur.com/cXVqitT.png?1)

*2) ownProps?: Object*

If your mapDispatchToProps function is declared as taking two parameters, it will be called with dispatch as the first parameter and the props passed to the wrapper component as the second parameter, and will be re-invoked whenever the connected component receives new props.

The second parameter is normally referred to as ownProps by convention.

![React-Redux Docs Example #2](https://i.imgur.com/ljQwLWq.png?1)

