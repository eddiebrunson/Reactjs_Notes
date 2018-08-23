# React Notes

![](http://progressed.io/bar/55?title=Progress)

---

### What Makes React Great?

Top 3 Reasons:

* compositional model
* the way data flows through a component 
* React is really just JavaScript


**Composition:** to combine simple functions to build more complicated ones

### Benefits of Composition:

--> the concept of composition is such a large part of what makes React awesome and incredible to work with. 

--> Remember that composition is just combining simple functions together to create complex functions.

--> There are couple of key ingredients here that we don't want to lose track of:

* simple functions
* combined to create another function

Instead of composing functions to get some value we will be composing functions to get some UI. 

And here's some code examples! :+1:

Composition is built from *simple* functions. Let's look at an example:

```javascript 
function getProfileLink (username) {
	return 'https://github.com/' + username
 }
```

```javascript
function getProfilePic (username) {
	return 'https://github.com' + username + '.png?size=200'
}
```

The above functions are *simple functions*, so to compose them, we just combine them together inside another function:

```javascript 
function getProfileData (username) {
	return {
		pic: getProfilePic(username),
		link: getProfileLink(username)
	}
}
```

Remember a good function should always follow the **"DOT"** rule:

Do one thing
___

### Rending UI with React 

--> React uses JavaScript objects to create React elements to describe what we want the page to look like and React is in charge of generating the DOM node to achieve the result

--> Note the difference between *imperative* and *declarative* code. 

**Imperative:** is when you list out the steps for the code 

**Declarative:** is when you declare exactly what you want the code to do 

So, in other words we aren't telling React what to do; but rather writing React elements that describes what the page should look like, and React does all the implementation work to get it done. 

--> When creating React elements it's important to remember that we are describing DOM nodes and not HTML strings

--> Virtual DOM is not real DOM elements that we are creating instead it's just objects that describe real DOM nodes

---
When we call React.creatElement we haven't actually created anything in the DOM yet

*Note:* You can't use the default **'for'** attribute. Just like you have to use className instead of Class, you have to use **htmlfor** instead of **for**. B/c **'for'** is a reserved word in JavaScript. 

--> React's .createElement() method to construct a "React element"

--> The .createElement() method has the following signature:

```JavaScript
React.createElement ( /*type*/, /*props*/, /*content*/);
```

* **type**- either a string or a React Component 

--> this can be a string of any existing HTML elements (eg. 'p', 'span', or 'header') or you could pass a React component 

* **props**- either null or an object 
--> this is an object of HTML attributes and custom data about the elements 

* **content-null**- a string, a React Element, or a React Component. Anything that you pass here will be the content of the rendered element. This can include plain text, JavaScript, or other React elements, etc. 
___

### Nesting-

--> React is a library for creating user interfaces. We can nest elements inside other elements 

--> Instead of writing child elements one by one, React let's us provide an array of elements to use as children. 

**Note:** when using an Array as children React will complain if you don't give it a *key* 

```JavaScript
React.craeteElement(li, {key: person.name}, person.name)
```

--> the *key* prop helps keep track of changes

Example:

```JavaScript
import React from 'react'
import ReactDOM from 'react-dom'

const people = [
   { name: 'Micheal' },
   { name: 'Ryan' },
   { name: 'Tyler' }   
]
```

```JavaScript
const element = React.createElement ( 'ol', null people.map((person, index) => (React.createElement('li', {key: index}, person.name)
))
)

ReactDOM.render(
   element, 
   document.getElementById('root')
)
```

---

**Caveat:** Always start component names with a capital letter

.createElement() returns one root element

JSX get complied down to calls to React's *.createElement()* method that outputs HTML to be rendered in the browser

**Note:** Single Responsibility Principle: is a CS principle that states that every module or class should have responsibility over a single part of the functionality provided by the software. 

**"A Class should only have one reason to change"** 

---

Webpack- is a complier which takes JSX code and complies it down to real JavaScript code that we can actually run in the browser

### Composition over Inheritance 

* Revisit 
*
*
*

---

**3 new concepts of React:**

* props- allows you to pass data into your components 
* Functional Components- an alternative way to create components
* Controlled Components- allow you to hook up the forms in your application to your component state

--> The way you build a React app is by building a bunch of smaller React Components and then composing them together 

--> We can think of passing *props* to components just as we pass arguments into functions. Just as we can access arguments passed into a regular JavaScript function, we can access a component's prop with **this.props** or props in the stateless functional components 

--> When passing in a prop to a prop, you just type out the name of the prop as if it's a regular HTML attribute.

--> A **prop** is any input you pass to a React component. Just like an HTML attribute, a prop name and value are added to the component. 

**Caveat:** Components must return a single root element. This is why we add a *<div>* to contain all the elements. 

All props are stored in *this.props* object. So to access this text prop from inside the component, we'd use this.props.text 

---

### Stateless Functional Components & props 

Stateless Functional Components are, stateless because these components do not have to worry about managing changing data. They just display the data. 

:question: When is it appropriate to use a Stateless Functional Component?

:white_check_mark: When all the component needs is a **render** method

--> If a component is only using a **render** method to display content, then it can be converted into a Stateless Functional Component. 


### Add State to a Component 

State is a key property of React components. Being familiar with how state is used and how state is set and reset will help streamline building the UI of your App. 

---

### Controlled Components 

-components which renders a form, but the source of truth for that form state lives inside of the component state rather than inside of the DOM. 

--> With Controlled Components our form state lives inside of the component. Because of this, we can easily update our UI based on that form state. 

--> Object destructuring- revisit 

---

Notes from [Facebook](https://reactjs.org)

### Converting a Function to a Class

1. Create a ES6 class with the same name that extends **React.Component** 
2. Add a single empty method to it called **render()**
3. Move the body of the function into the render() method
4. Replace **props** with this.props in the render() body
5. Delete the remaining empty function declaration 

### Adding local state to a Class

--> to use state correctly you do **not** modify state directly 
--> so we use setState()

// wrong

```JavaScript 
this.state.comment ='Hello';
```

// correct 

```JavaScript 
this.setState({comment: 'Hello'});
```

The only place where you can assign **this.state** is the constructor.

--> State, is often called local or encapsulated. It's not accessible to any component other than the one that owns and sets it. 

### Handling Events 

--> React events are named using camelCase, rather than lowercase 
--> With *JSX* you pass a function as the event handler rather than a string. 

* **e**, is a synthetic event

* When using React you should generally not need to call addEventListener, to add listeners to a DOM element after it is created. Instead, just provide a listener when the element is initially rendered. 

* When you define a component using an ES6 class, a common patter is for an event handler to be a method on the class. For, example, this toggle component renders a button that lets the user toggle between "on" and "off" states.

* Experimental syntax- property initializer syntax to correctly bind callbacks:

                      or 
   you can use an arrow function in the callback, although this can cause extra re-rendering so it's recommended to use the property initializer syntax. 
---

### Conditional Rendering 

Works the same way conditions work in JavaScript

---

### Rendering Multiple Components 

-using JavaScript **map()** function 
a "key", is a special string attribute you need to include when creating lists of elements. 

--> **Keys** help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity. 

--> The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use **IDs** from your data as keys.

--> When you don't have stable IDs for rendering items you may use the item index as a key as a last resort. 

---

### Controlled Components

"Single Source of truth"

---

### Composition vs. Inheritance

React- recommends to use composition over inheritance


---

### Thinking in React 

Don't use state for static version. State is reserved only for interactivity, that is, data that changes over time. 

---

### Update state with setState

--> Cannot update state directly, because React will have no idea that the state of your component actually changed. 

--> To solve this problem React gives us a helper method called **setState**

There are two ways to use setState:

1. by passing setState a function, the function will be passed the previous state as its first argument. 
   * the object returned from this function will be merged with the current state to form the new state of the component. 

**function**
```JavaScript
this.setState (() => ({
  count:1
}))
```
**function passed the previous state as its first argument**

```JavaScript
this.setState((prevState) => ({
  count: prevState.count + 1
}))
```

2. pass in a object

   * the object will be merged with the current state to form the new state of the component. 

   ex. 

```JavaScript
this.setState ({
  username: 'Tyler'
})
```

--> You will want to use the functional setState when the new state of your component depends on the previous state

*for anything else use the object setState*

**Your UI is just a function of your state**

---

### How state is set

Since state reflects mutable information that ultimately affects rendered output, a component may also update its state throughout its lifecycle using **this.setState**

---
**Most recent notes-- will go back and add missing notes soon**

### Redux Middleware

--> Redux makes state management more predictable: in order to change the store's state, an action describing that change must be dispatched to the reducer. 

--> In turn,the reducer produces the new state. This new state replaces the previous state in the store. So the next time **store.getState** is called, the new, most up-to-date state is returned.

--> In Between the dispatching of an action and the reducer running, we can introduce code called middleware to intercept the action before the reducer is invoked. 

* What's great about middleware is that once it receives the action, it can carry out a number of operations, including:

   * producing a side effect (e.g., logging information about the store)
   * processing the action itself (e.g., making an asynchronous HTTP request)
   * redirecting the action (e.g., to another piece of middleware)
   * dispatching supplementary actions

...or even some combination of the above! Middleware can do any of these before passing the action along to the reducer.

---

### Where Middelware Fits

Originally, in the example code structure **checkAndDispatch()** function had to run before **store.dispatch()**. Why? Because, when **store.dispatch()** is invoked, it immediately calls the reducer that was passed in when **createStore()** was invoked. 

In the beginning the **dispatch()** function looked this and it is very similar to the real Redux **dispatch()** function: 

```JavaScript 
const dispatch = (action) => {
  state = reducer(state, action)
  listeners.forEach((listener) => listener())	
} 
```

Calling **store.dispatch()** will immediately invoke the **reducer()** function. There is no way to run anything in between the two function calls. So that's why you have to make **checkAndDispatch()** so that you can run verification code before calling **store.dispatch()**. 

However, that is maintainable. 

With Redux's middelware feature, we can run code *between* the call to **store.dispatch() and **reducer()**. The reason this works, is because Redux's version of **dispatch()** is a bit more sophisticated, because middelware functions are provided when you create the store. 

```JavaScript 
const store = Redux.createStore( <reducer-function>, <middleware-function> )
```
Redux's **createStore()** method takes the reducer function as its first argument, but then it can take a second argument of the middleware functions to run. Because we set up the Redux store with knowledge of the middleware function, it runs the middelware function between **store.dispatch()** and the invocation of the reducer. 

___

### Applying Middelware 

To implement middleware into a Redux app all you have to do is pass it in when creating the store. More specifically by passing in the **applyMiddleare()** function as an optional argument into **createStore()**. Here's **applyMiddleware()** signature: 

```JavaScript
applyMiddleware(...middlewares)
```

Note the *spread* operator on the middlewares parameter. This means that you can pass in as many different middleware as you want. Middleware is called in the order in which they were provided to **applyMiddleware()**

Now, to create a Redux store that uses the **checker** middleware, you can use the following: 

```JavaScript
const store = Redux.createStore(rootReducer, Redux.applyMiddleware(checker))
```

---

:red_circle: **Functions Returning Functions** :red_circle:

Redux middleware leverages a concept called **higher-order functions**. A higher-order function is a function that either: 

   * accepts a function as an argument 
   * returns a function 

High-order functions are a powerful programming technique that allow functions to be significantly more dynamic. The **createRemoveButton()** function is a higher-order function because the **onClick** parameter is expected to be a function because **onClick** is set up as an event listener callback function.

For a refresher on higher-order function check out lesson 2 in Object-Oriented JavaScript. 

--> Any Middleware you supply as the second argument to **Redux.createStore()** will be run before the reducer is run. 

### A New Middleware: Logging

You can use multiple middleware functions in a single application. 

**logger** will log out information about the state and action. 

--> The benefits of this **logger()** middleware function are huge while developing the application. Using this middleware to intercept all dispatch calls and log out what the action is that's being dispatched and what the state changes to *after* the reducer has run. Being able to see this kind of information will be immensely helpful while you are developing your app. You can us this information to help you know what's gong on in your app and to help you track down any pesky bugs that creep in. 

--> You don't have to use middleware in your Redux applications, but you can if you want to. And what's awesome is that you can supply one or many middleware functions to **Redux.applyMiddleware()**!

  * **Redux.applyMiddleware()** can accept multiple arguments
  * Middleware is optional 
  * Middleware can be considered a third-party extension point between dispatching and having the action reach the reducer

  ---

  ### Summary

--> Middleware is the suggested way to extend Redux with custom functionality.

Middleware is added to the Redux store using **Redux.applyMiddleware()**. You can only add middleware when you initially create the store:

```JavaScript 
const store = Redux.createStore( <reducer-function>, Redux.applyMiddleware(<middleware-functions>) )
```

---

### Further Research 

[Middleware Docs](https://redux.js.org/advanced/middleware)

---

### Redux with React 

To move away from the application being plain HTML and convert it to being powered by React. To do that, you will have to add a number of libraries:

  * react (npm i react)
  * react-dom (npm i react-dom)
  * babel (npm i babel) deprecated 

  The following are the needed packages:

<script src="https://unpkg.com/react@16.3.0-alpha.1/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@16.3.0-alpha.1/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>




### Combining React and Redux 

Now it's time to convert HTML to a React application by connecting the React Components to a React application. 

---

### Summary 

Here code organization was improved and reusable parts of code were separate. 

## Asynchronous Redux 

Interacting with an external database with an API. 

--> How to make *asynchronous* requests in Redux

The way Redux works is:

   * **store.dispatch()** calls are made
   * if the Redux store was set up with any middleware, those function are run
   * then the reducer is invoked 
---

### External Data

--> link to external API which will call methods such as **API.fetchGoals** which will return a promise that after 2 seconds will resolve a goal 

--> the use case to handle is if the return fails 

--> Next, you must tell the Redux store about the data

--> Then create a brand new action creator called **receiveDataAction**

**Promise-Based API**

The methods in the provided API are all Promise-based. Let's take a look at the .fetchTodos() method:

```JavaScript 
API.fetchTodos = function () {
  return new Promise((res, rej) => {
    setTimeout(function () {
      res(todos);
    }, 2000);
  });
};
```

* Since the API is Promise-based, we can use Promise.all() to wait until all Promises have resolved before displaying the content to the user.

* **Promises are asynchronous**, and this lesson is all about working with asynchronous data and asynchronous requests.


---

### Summary 

Learned how to work with an external API. Also how to add a new action (**RECEIVE_DATA**), create a new action creator, and build a new reducer. Which all handle different states our app can be in while getting remote data:

  * before the app has the data 
  * while the app is fetching the data
  * after the data has been received 

### Optimistic Updates 

---> When dealing with asynchronous requests, there will always be some delay involved. If not taken into consideration, this could cause some weird UI issues. 

--> For example, let’s say when a user wants to delete a todo item, that whole process from when the user clicks“delete” to when that item is removed from the database takes two seconds. If you designed the UI to wait for the confirmation from the server to remove the item from the list on the client, your user would click “delete” and then would have to wait for two seconds to see that update in the UI. That’s not the best experience.

--> Instead what you can do is a technique called optimistic updates. Instead of waiting for confirmation from the server, just instantly remove the user from the UI when the user clicks “delete”, then, if the server responds back with an error that the user wasn’t actually deleted, you can add the information back in. This way your user gets that instant feedback from the UI, but, under the hood, the request is still asynchronous.

### Summary 

Concepts covered:

   * removed Todos and Goals 
   * toggle the state of a Todos
   * save a new Todo or Goal 

--> Here changes are done *optimistically* therefore the assumption is taken that the change will succeed correctly on the server, so the UI is immediately updated, and if there is an error it will revert back to the original state if the API returns an error. 

--> More realistic and dynamic user experience 

### Thunk 


Best to keep UI Logic Component separate from the data fetching API logic in a Action creator. Therefore, the action creator will be responsible for fetching the data it needs to create the actual action. 

For Example the code for removing a todo item looks like this:

```JavaScript
removeItem(item) {
  const { dispatch } = this.props.store

  dispatch(removeTodoAction(item.id))

  return API.deleteTodo(item.id)
    .catch(() => {
      dispatch(addTodoAction(item))
      alert('An error occured. Try again.')
    })
  }
}
```

In the above code snippet component-specific code is mixed in with API-specific code.

--> By moving the data-fetching logic from the component to the action creator, the final **removeItem()** method looks like this:

```JavaScript
removeItem(item) {
  const { dispatch } = this.props.store

  return dispatch(handleDeleteTodo(item))
}
```

Now the **removeItem()** function only has one task; dispatching that a specific item needs to be deleted. 


Now, the **handleDeleteTodo** action creator needs to make an asynchronous request before it returns the action. 
 



### Benefits of Thunks

--> Out of the box, the Redux store can only support the synchronous flow of data. While, middleware, like **thunk** allows for asynchronicity in a Redux application. 

--> Thunk is basically a wrapper for the store's **dispatch()** method; rather than returning action objects, thunk action creators are used to dispatch functions or event Promises. 

* Thunk middleware can be used to delay an action dispatch, or to dispatch only if certain conditions are met. The logic lives inside action creators rather than inside components. 


___

### Project Walkthrough 

To make the understanding of React and Redux, stronger there is a project called "Chirper" which is a walkthrough project. It should be used to model after for the "Would you Rather" Project. 

Building this walkthrough project will help with understanding the importance of improving predictability of an application's state; establishing strict rules for getting, listening, and updating the store; and identifying what state should live inside of Redux and what state should live inside of React components. 


**Important to plan our the architecture of the application before starting to code**



### A Guide for Planning Stages of Your Project 

1. Identify What Each View Should Look Like
2. Break Each View Into a Hierarchy of Components 
3. Determine What Events Happen in the App
4. Determine What Data Lives in the Store


### Planning Stage: Steps 1&2 - Break Down Views and Components 

**View for the Dashboard Page**

-displays the navigation and tweets

### Dashboard View Requirements 

* is located at the home route **(/)**
* shows tweets sorted from most recently added at the top, to oldest at the bottom
* each tweet will show:
  * the author
  * the time stamp 
  * who the author is replying to 
  * the text of the tweet 
  * a reply button - with the number of replies (if higer than 0)
  * a like button - with the number of likes (if higher than 0)

#### View for the Tweet Page

#### Tweet Page View Requirements 

  * is located at /tweet/:id
  * shows an individuals tweet
    * the author
    * the time stamp 
    * a reply button - with the number of replies (if higher than 0)
    * a like button - with the number of likes (if higher than 0)

  * has a reply form 
  * shows all replies 

#### View for Creating a New Tweet 


#### The New Tweet View Requirements 

  * is located at **/new**
  * has a textbox for adding a new tweet

#### View Recap 

The 3 views needed for this app:

  * Dashboard 
  * Tweet 
  * New Tweet 

#### Stepm 2: Break Each View Into a Hierarchy of Components 
  * draw boxes around every component 
  * arrange our components into a hierarchy 

  ---

  Components let you split the UI into independent, resuable chunks. 

  Each view typically has a component that represents that view 

  Presentational Components don't know where their data comes from 

  Components that are connected to the store are called "containers"

--> Components are best used to isolate specific sections of the app, either as access data (containers) or focused on the UI (presentational).

---
#### Components for the Dashboard View 

The Dashboard can be broken up into  React Components 

  * App - the overall container for the project 
  * Navigation - displays the navigation 
  * Tweets List - reponsible for the entire list of tweets
  * Tweet - in charge of displaying the content for a single tweet 

#### Components for the Tweet View 

The Tweet view can be broken up into React Components 

  * App - the overall container for the project 
  * Navigation - displays the navigation 
  * Tweet Container - displays a list of tweets 
  * Tweet - displays the content for a single tweet 
  * New Tweet - display the form to create a new tweet (reply)


#### Components for the New Tweet View 

The New Tweet view can be broken up int React Components 

  * App - the overall container for the project 
  * Navigation - displays the navigation 
  * New Tweet - display the form to create a new tweet 

#### All Components 

This application will have the following components:
  
  * App 
  * Navigation 
  * Tweets List 
  * Tweet Container 
  * Tweet 
  * New Tweet 

The component hierarchy tells us which components will be used inside of other components. It gives use the skeleton of our app. These are presentational components. 

Right now there is no need to focus on which components will later becomes containers. 

The above steps are just focused on React app, but we haven't gotten to using Redux yet. 

As Redux doesn't care how your application looks or what components it uses. Redux gives us a way to manage the *state* of the application in a predictable way. 

---

### Planning Stage: Step 3 -Determine Events in the App

#### Determine What Events Happen in the App

Now we need to determine *what* is happening in each component. So it's time to determine what actions the app or the user is performing on the data. Is the data being set, modified, or deleted?... then you will need an action to keep track of that event! 

**Actions are bold text**

#### Tweets List Component 

The only information that we see is that we'll have to get a list of all the tweets. So for this component we just need to: 
  
  * get the **tweets**

The action type for this event will be 

GET_LIST_OF_TWEETS or GET_DATA

#### Tweet Component 

* We get a particular tweet from a list of **tweets** 
* We get the replies to a specific tweet from a list of **tweets**

#### New Tweet Components 

* We get this **authedUser** so the user can create a new **tweet** 

* We set the **text of the new tweet**

Next, we need to determine which of the above data will live in the store.

### Planning Stage: Step 4 - Data and the Store 

The main problems that Redux and the react-redux bindings is meant to solve the following:

  * Propagation of props through the entire component tree
  * Ensuring consistency and predictability of the state across the app. 

:arrow_right: According to **Dan Abramov**, the creator of Redux, we should follow the following principle for determining whether to store a piece of data in the store or in a React component: 

   :::: "Use Redux for state that matters globally or is mutated in complex ways... The rule of thumb is: do whatever is less awkward."

Review [Organizing State](https://redux.js.org/faq/organizingstate) and [How to choses between Redux's store and React's state?](https://github.com/reduxjs/redux/issues/1287)

Text of the new tweet Used by: New Tweet Component 

This piece of data is not used by multiple components and is not mutated in a complex way. That means that it's a great candidate for component state instead of app state that resides in the store. 

Tweets Used by: Dashboard Component, Tweet Page Component, Tweet Component 

The the Tweet Page Component, we need to show the reply tweets. The started code in **_Data.js** shows how tweets are stored in the database:

```JavaScript 
let tweets = {
  tweetId: {
    id: tweetId,
    text: tweetText,
    author: userId,
    timestamp: timestamp,
    likes: [userId1, userId2],
    replies: [tweetId1, tweetId2],
    replyingTo: tweetId_OR_null
  }
};
```

















