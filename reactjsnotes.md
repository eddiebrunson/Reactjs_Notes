# React Notes

![](http://progressed.io/bar/30?title=Progress)

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

  * react 
  * react-dom
  * babel 

  












