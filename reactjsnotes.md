# React Notes

![](http://progressed.io/bar/25?title=Progress)

---

### What Makes React Great?

Top 3 Reasons:

* compostional model
* the way data flows through a component 
* React is really just JavaScript


**Composition:** to combine simple functions to build more comlicated ones

### Benefits of Composition:

--> the concept of composition is such a large part of whwat makes React awesome and incredible to work with. 

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

--> React uses JavaScript objects to create React elements to describe what we want the page to look like and React is in charge of generating the DOM node to achieve the restult

--> Note the difference between *impreative* and *declarative* code. 

**Imprerative:** is when you list out the step for the code 

**Declarative:** is when you declare exactly what you want the code to do 

So, in other words we aren't telling React what to do; but rather writing React elements that decribes what the page should look like, and React does all the implementation work to get it done. 

--> When creating React elements it's important to remember that we are describing DOM nodes and not HTML strings

--> Virtual DOM is not not real DOM elements that we are creating instead it's just objects that describe real DOM nodes

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

JSX get complied down to calls to React's *.createElement()* method tat outputs HTML to be rendered in the browser

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

--> We can think of passing *props* to components just as we pass arguements into functions. Just as we can access arguments passed into a regular JavaScript function, we can access a component's prop with **this.props** or props in the stateless functional components 

--> When passing in a prop to a prop, you just type out the name of the prop as if it's a regular HTML attribute.

--> A **prop** is any input you pass to a React component. Just like an HTML attribute, a prop name and value are added to the component. 

**Caveat:** Components must return a single root element. This is wehy we add a <div> to contain all the elements. 

All props are stored in *this.props* object. So to access this text prop from inside the component, we'd us this.props.text 

---

### Stateless Functional Components & props 

Stateless Functional Components are, stateless because these components do not have to worry about managing changing data. They just display the data. 

:question: When is it appropriate to use a Stateless Functional Component?

:white_check_mark: When all the component needs is a **render** method

--> If a component is only using a **render** method to display content, then it can be converted into a Stateless Functional Component. 


### Add State to a Component 

State is a key property of React components. Being familar with how state is used and how state is set and reset will help streamline building the UI of your App. 

---

### Controlled Components 

-components which renders a form, but the source of truth for that form state lives inside of the component state rather than inside of the DOM. 

--> With Controlled Components our form state lives inside of the component. Because of this, we can easily update our UI based on that form state. 

--> Object destructuring- revisit 

---

Notes from [Facebook](facebook.github.io)

### Converting a Function to a Class

1. Create a ES6 class with the same name that extends **React.Component** 
2. Add a single empty method to it called **render()**
3. Move the body of the function into the render() method
4. Replace **props** with this.props in the render() body
5. Delete the remaining empty function declaration 



