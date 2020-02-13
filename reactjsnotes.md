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


Revisit Real World Redux part 5. Planning stage: Step 4 to 15. Course summary.

### React Native 

#### Lesson 1: Up and Running with React Native 

Course Map
Welcome! This course covers the React Native framework. Here's a quick breakdown of what the course looks like:

* Lesson 1 illustrates the benefits of using React Native to build native applications, as well as how to set up an effective dev environment.
* Lesson 2 compares the main ideological and API differences between React and React Native.
* Lesson 3 details styling and layout patterns for React Native applications.
* Lesson 4 examines routing patterns and strategies.
* Lesson 5 introduces native functionality (e.g., geolocation, notifications, etc.) and preparation of applications for the app store.

--> In-Class Project
During this course, you'll follow along and create a daily fitness-tracking application, UdaciFitness. You'll tie in what you've learned from React Fundamentals as well as React & Redux, then leverage React Native to create a fully functional mobile application!


---

#### 2. What is React Native and Why does it exist?

React Native under the Hood
When React was first introduced, a big selling point was the Virtual DOM. The idea is pretty standard in most UI libraries now, but when it first came out, it was groundbreaking! We can look at what exactly the Virtual DOM is by breaking down the process of what happens when you call setState().

The first thing React does when setState() is called is merge the object passed to setState() into the current state of the component. This will kick off a process called reconciliation. The end goal of reconciliation is to update the UI based on this new state in the most efficient way possible. To do this, React will construct a new tree of React elements (which you can think of as an object representation of your UI). Once it has this new tree, React will "diff" it against the previous element tree in order to figure out how the UI should change in response to the new state. By doing this, React will then know the exact changes which occurred, and by knowing exactly what changes occurred, it will able to minimize its footprint on the UI by only making updates where absolutely necessary.

This process of creating an object representation of the DOM is the whole idea behind the "Virtual DOM". Now, what if instead of targeting and rendering to the DOM, we need to target and render to another platform -- say iOS or Android. Theoretically, the DOM is just an implementation detail. Besides the name itself (which, in my opinion, was more of a marketing ploy than anything), there's nothing that couples the idea of the Virtual DOM to the actual DOM. This is the exact idea behind React Native. Instead of rendering to the web's DOM, React Native renders to native iOS or Android views. This allows us to build native iOS and Android applications just by using React Native.


Summary
React Native's "learn once, write anywhere" approach allows us to use the same principles that we know to develop for both web and native platforms. After all, under the hood, many of the same principles of the Virtual DOM, reconciliation, and diffing algorithm apply whether it's a web application built with React or a mobile application built with React Native.

Further Research
[Bridging in React Native](https://tadeuzagallo.com/blog/react-native-bridge/)
[12 Common Questions from Working with React Native](https://medium.com/dailyjs/12-common-questions-about-react-native-74fc9ba49b17)

___

#### Dev Environment setup



**Create React Native App**

When we build our app throughout this course, we'll be building it for both Android and iOS. One of the puzzles at hand is that we'll need to support two separate development environments: iOS uses Xcode, and Android uses Android Studio. This introduces a lot of complexity into this course; after all, both Xcode and Android Studio could probably each be their own set of courses!

Luckily for us, there's a new tool we can use that will allow us to develop for both Android and iOS without ever opening up Android Studio or Xcode. It's called, not surprisingly, Create React Native App. It's similar to Create React App in that all you have to do is install the CLI via NPM. Then, via the CLI, you can easily scaffold a brand new React Native project.

Just like Create React App, there are pros and cons to using Create React Native App (CRNA). First, the pros.

#### Create React Native App Pros

The obvious one is that Create React Native app minimizes the amount of time it takes to create a "hello world" application. 

The fact that you can run a command in your terminal and 15 seconds later have a project that run on both Android and iOS using JavaScript is pretty incredible. Next, and we'll look deeper into this one later on, Create React Native App allows you to easily develop on your own device. 

This way, any changes you make in your text editor will instantly show on the app running on your local phone. Next, and this is something I mentioned earlier, with Create React Native App you just need one build tool. You don't have to worry about Xcode or Android Studio. Lastly, there's no lock in. Just like Create React App, you can "eject" at anytime.

#### Create React Native Cons

Now, there are some cons, and granted they're pretty minor, but they're good to be aware of. First, if you're building an app that's going to be added to an existing native iOS or Android application, Create React Native App won't work. Second, if you need to build your own bridge between React Native and some native API that Create React Native App doesn't expose (which is pretty rare), Create React Native App won't work.

Let's jump right in!

#### Install Create React Native App
In order to use Create React Native App, go ahead and install it once globally:

`npm install -g create-react-native-app`
Alternatively, feel free to use yarn as well (visit here for setup instructions):

`yarn global add create-react-native-app`
⚠️ Using Yarn ⚠️
Create React Native App does not currently work well with NPM v5, due to bugs in NPM. While there should be no issues with NPM v3 or v4, we'll be using yarn from here on out just to be safe.


---

#### Expo 

Expo is a service that makes just about everything involving React Native a whole lot easier. The idea behind Expo is that there's no need to use Android Studio or Xcode. What's more: it even allows us to develop for iOS with Windows (or even Linux)!

With Expo, you can load and run projects built by Create React Native App with the same JavaScript you already know. There's no need to compile any native code. And much like Create React App, using Expo with Create React Native App lets us get an application up and running with almost no configuration.

We'll be relying on Expo heavily in this course. First things first: you need to install Expo. Head to the app store and install the Expo mobile app for your device:

[Expo on Google Play (Android)](https://play.google.com/store/apps/details?id=host.exp.exponent)
[Expo on the App Store (iOS)](https://itunes.apple.com/us/app/expo-client/id982107779)

---

#### Simulators 📱

Expo together with Create React Native App is the fastest way to get up and running, but there are also other ways to start building your projects, as well. If you're looking to integrate React Native into an existing app, or if you've ejected your app from Create React Native App, feel free to follow the Building Projects with Native Code tab from the React Native docs. The guide also sets up iOS and Android simulators, allowing you to view your mobile apps right on your machine!

We'll be utilizing both iOS and Android simulators in the interest of demoing projects in this course, but they are completely optional in getting started.

#### Installing Simulators

🔷 iPhone Simulator 🔷

iOS apps can only be developed on a Mac unless you have a virtual machine set up on your machine. To set up the iPhone simulator on your Mac, follow these instructions:

1) Go to the App Store.

2) Download Xcode.

3) Follow the installation instructions.

4) Open Xcode and install additional software if prompted to do so.

If you already have Xcode installed, please make sure that you update it. Then, open it to make sure no further updates are needed. Most problems with setting up your React Native development environment can be solved this way.

5) Open Xcode and go to "Preferences."

6) Go to the "Locations" panel and select the most recent version in the "Command Line Tools" drop-down list.

7) That’s it!

____


🔷Android Simulator 🔷

The setup is kind of complicated, but we'll get through it together.

Part 1

1) Install a recent version of the Java SE Development Kit(JDK).

2) Install Android Studio Choose a "Custom" setup when prompted. Make sure the boxes next to all of the following are checked:

Android SDK
Android SDK Platform
Performance (Intel ® HAXM)
Android Virtual Device
3) Click "Next".

4) Launch Android Studio.

5) Click on "Configure" and select "SDK Manager".

6) Select the "SDK Platforms" tab.

7) Put a checkmark next to "Android API 28", "Android 8.0", "Android 6.0 (Marshmallow)," "Android 7.0," and "Android 7.1.1."

8) Go to the "SDK Tools" tab.

9) Put checkmarks next to :

Android SDK Build-Tools
Android SDK Platform-Tools
Android SDK Tools
Android Emulator
Intel x86 Emulator Accelerator (HAXM installer)
Under the Support Repository, put a checkmark at "Android Support Repository"
10) Click "OK".

11) Follow the on-screen directions to install the requested components.

12) If you are on a Windows machine, please install the Intel x86 Emulator Accelerator through the Android SDK Manager, if prompted.

13) If you are on a Windows or Linux machine, please make sure to enable Virtualization Technology in your BIOS settings.

14) If you are on a Windows machine:

a) Open Android Studio. Go to "File" and then click "Project Structure." Make sure this box is checked: "Use embedded JDK(recommended)." Please copy the Android SDK location (e.g. C:\User\userName\AppData\Local\Android\Sdk); we'll be using it shortly.

b) Open the System Control Panel. Click on "Advanced system settings." Click on "Environment Variables." Create a new variable ANDROID_HOME and set it to the Android SDK location you copied before.

Create a new variable JAVA_HOME and set it to the installation path for the Java Development Kit (e.g. C:\Program Files\Java\jdk1.8.0_171).

15) If you are on a macOS or Linux:

a) Open Android Studio. Click on "Configure" and select "SDK Manager" again. Go to Appearance & Behavior -> System Settings -> Android SDK.

b) Look at the path that’s filled in for the "Android SDK Location" section. It should be something like: /Users/yourName/Library/Android/sdk. If you are on macOS or Linux, add the Android SDK location to your PATH using ~/.bash_profile or ~/.bash_rc (e.g. echo 'export PATH=$PATH:~/Library/Android/sdk/'>>~/.bash_profile).

c) On macOS, you will also need to add platform-tools to your ~/.bash_profile or ~/.bash_rc (e.g. echo 'export PATH=$PATH:~/Library/Android/sdk/platform-tools' >>~/.bash_profile, source ~/.bash_profile).

d) Make sure that you can run adb from your terminal.

**Part 2**

You have a choice of either using the Android Studio Emulator or Genymotion as your simulator. You don't have to install both.

Directions for Setting up the Android Studio Emulator

1) Open Android Studio.

2) Click "Start a new Android Studio project". You don't need to change any of the settings; just click through to "Finish". Click "Finish".

3) Once a new project is created, look at the messages inside the Gradle Console.

If you see any error messages that prompt you to install additional software, please install it.

4) Select "Tools" --> "AVD Manager". Ensure that there's a checkmark next to "Enable ADB Integration".
5) Click "Create Virtual Device".

6) Select the system image you want and click "Download".

7) Once the download completes, click "Next" and "Finish".

8) Click the play button.

**Directions for Setting up Genymotion**

Download and install Genymotion(it is free for personal use).
Set up an Android emulator by selecting the type of phone you want to emulate and wait for the setup to complete.
Open Genymotion and navigate to "Settings" and then "ADB". Select "Use custom Android SDK tools," and update it with your Android SDK location (e.g. /Users/yourName/Library/Android/sdk).
Restart GenyMotion.
Got to "Settings". Go to "ADB" and make sure there is a checkmark next to "Android SDK successfully found".
Run npm install -g exp to install exp globally.
Run exp path. This will save your PATH environment variable so that XDE knows where to find your Android tools.
Close Android Studio if you still have it open. Check to make sure that Android Studio is no longer running.
Start the GenyMotion Emulator by clicking "Start".
The majority of these instructions are from the Genymotion documentation.

####💡 Bundling Error (Unexpected Token)💡
If you're seeing bundling errors while attempting to run a simulator, try changing your Babel preset for React Native to version 2.1.0. Then, remove your node-modules directory, reinstall with npm install, and run the simulator again. For more information, check out this post on Stack Overflow.

####💡 Error: Cannot Connect to Daemon💡
If you see this message "Couldn't start project on Android: could not install *smartsocket* listener: cannot bind to 127.0.0.1:5037: Only one usage of each socket address (protocol/network address/port) is normally permitted. Could not read ok from ADB Server. Failed to start daemon. Error: cannot connect to daemon," please restart your computer and try again.
A Note About Expo

Expo is a great tool, but it can be buggy. If it's not working, try using the Expo XDE. To do that, install Expo XDE and follow the instructions provided in the documentation. To run a project, click “Open an Existing Project,” click “Device,” and either run it on your emulator or your physical device.

If you see an orange message at the top asking you to update the Expo XDE, please make sure you install the update. Otherwise, Expo XDE may not work correctly.
If you're trying to run your project on the iOS simulator and are getting the error message below, please go to the App Store and update your Xcode. Then, open Xcode and install additional required software, if prompted. Open your project's app.json file and edit the value of sdkVersion to match the required version listed in the error message (e.g. 21.0.0). Then, run rm -rf .node_modules && yarn install && yarn run ios --reset-cache.

---

#### The Environment

When creating an app with Create React Native App, what type of support should you expect?

ES5 and ES6 support
Object Spread Operator
Asynchronous functions
JSX (this is React, after all!)
Flow
Fetch

Since we are using purely JavaScript to build mobile apps, this list should come as no surprise! Since Create React Native App ships with Babel, feel free to check out the full list of supported transformations.
Before we start actually building our app, there are some files that are necessary for the project, but aren’t necessary for you to fully understand. Because of this, we’ll just give you the code and you can look over it if you’d like.

All three of these files will live inside of a utils folder. So first, create a folder called utils at the root of your project.

Next, you’re going to create three files inside of your utils folder.

colors.js
helpers.js
_calendar.js (make sure to include the underscore!)



Paste the following code into your utils/colors.js file

// utils/colors.js

export const purple = '#292477'
export const gray = '#757575'
export const white = '#fff'
export const red = '#b71845'
export const orange = '#f26f28'
export const blue = '#4e4cb8'
export const lightPurp = '#7c53c3'
export const pink = '#b93fb3'
Next, paste the following code into utils/helpers.js

// utils/helpers.js

export function isBetween (num, x, y) {
  if (num >= x && num <= y) {
    return true
  }

  return false
}

export function calculateDirection (heading) {
  let direction = ''

  if (isBetween(heading, 0, 22.5)) {
    direction = 'North'
  } else if (isBetween(heading, 22.5, 67.5)) {
    direction = 'North East'
  } else if (isBetween(heading, 67.5, 112.5)) {
    direction = 'East'
  } else if (isBetween(heading, 112.5, 157.5)) {
    direction = 'South East'
  } else if (isBetween(heading, 157.5, 202.5)) {
    direction = 'South'
  } else if (isBetween(heading, 202.5, 247.5)) {
    direction = 'South West'
  } else if (isBetween(heading, 247.5, 292.5)) {
    direction = 'West'
  } else if (isBetween(heading, 292.5, 337.5)) {
    direction = 'North West'
  } else if (isBetween(heading, 337.5, 360)) {
    direction = 'North'
  } else {
    direction = 'Calculating'
  }

  return direction
}

export function timeToString (time = Date.now()) {
  const date = new Date(time)
  const todayUTC = new Date(Date.UTC(date.getFullYear(), date.getMonth(), date.getDate()))
  return todayUTC.toISOString().split('T')[0]
}
Finally, paste the following code inside of your utils/_calendar.js file



```JavaScript
// utils/_calendar.js

import { AsyncStorage } from 'react-native'
import { getMetricMetaInfo, timeToString } from './helpers'

export const CALENDAR_STORAGE_KEY = 'UdaciFitness:calendar'

function getRandomNumber (max) {
  return Math.floor(Math.random() * max) + 0
}

function setDummyData () {
  const { run, bike, swim, sleep, eat } = getMetricMetaInfo()

  let dummyData = {}
  const timestamp = Date.now()

  for (let i = -183; i < 0; i++) {
    const time = timestamp + i * 24 * 60 * 60 * 1000
    const strTime = timeToString(time)
    dummyData[strTime] = getRandomNumber(3) % 2 === 0
      ? {
          run: getRandomNumber(run.max),
          bike: getRandomNumber(bike.max),
          swim: getRandomNumber(swim.max),
          sleep: getRandomNumber(sleep.max),
          eat: getRandomNumber(eat.max),
        }
      : null
  }

  AsyncStorage.setItem(CALENDAR_STORAGE_KEY, JSON.stringify(dummyData))

  return dummyData
}

function setMissingDates (dates) {
  const length = Object.keys(dates).length
  const timestamp = Date.now()

  for (let i = -183; i < 0; i++) {
    const time = timestamp + i * 24 * 60 * 60 * 1000
    const strTime = timeToString(time)

    if (typeof dates[strTime] === 'undefined') {
      dates[strTime] = null
    }
  }

  return dates
}

export function formatCalendarResults (results) {
  return results === null
    ? setDummyData()
    : setMissingDates(JSON.parse(results))
}
```

#### Summary 

Create React Native App is similar to Create React App in that it scaffolds and builds a starter application with minimal configuration. This allows us to have an app up and running without the need for Xcode or Android Studio! Some of the benefits include:

Minimal "time to 'Hello World'"
Development on your own device via Expo
A single build tool
No lock-in (i.e., ejection at any time)
You can also set up simulators to aid in development as well. But regardless of which platform we choose to develop for (iOS, Android), and which environment we're in (Mac, Windows, Linux) -- we're just building with the same old JavaScript that we're used to!
