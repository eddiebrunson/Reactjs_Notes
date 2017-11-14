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

