---
title: JavaScript
---

JavaScript, mostly in the browser.

Related: [[React]] [[React Patterns]] [[React Native]]

## Useful Links

- [Cheat sheet for moving from jQuery to vanilla JavaScript \| Tobias Ahlin](https://tobiasahlin.com/blog/move-from-jquery-to-vanilla-javascript/)
- [Online Interactive JavaScript (JS) Cheat Sheet](https://htmlcheatsheet.com/js/)

## Terms

- *Initialize*
	- Assign a value to a variable when declaring it.
- *String Literal*
	- Zero or more characters enclosed in quotes.
	- `var myVar = "Hello World!";`
		- `myVar` is the string variable.
		- `"Hello World!"` is the string literal.
- *Escape*
	- "Escape" a quote from being considered as end of string with backslash (`\`.)
	- Alternatively, use different quote types.
	- Common escape sequences:
		- `\'` single quote
		- `\"` double quote
		- `\\` backslash
		- `\n` newline
		- `\r` carriage return
		- `\t` tab
		- `\b` backspace
		- `\f` form feed (?)
- *Bracket notation*
	- A way to get characters at a specific place within a string.
	- Zero-based indexing.
	- `var name = "Charles";`
	- `firstName[0]` equals "C."	
- *Functions*
	- Reusesable parts of code.
	- *Paramaters*
		- Variables that act as placeholders for function input.
	- *Arguments*
		- The actual values passed in the function call.
- *Scope*
	- The visibility of variables. 
	- *Global*
		- Variables defined outside of a function are global. They can be seen anywhere in the code.
		- Ommiting the `var` automatically creates a global variable. Always declare variables with `var`.
	- *Local*
		- Variables defined inside a function, as well as the function paramaters.
	- A local variable takes precedence over a global variable when two variables have the same name.
- *Properties*
	- Parts of an object.
	- Access with dot operator `.` or bracket notation `[]` (like an array). The two can be chained together for complicated trees.
	- Use dot `.` when you know the name of the property. 
	- Bracket notation `[]` is required when the propert has a space in the name.
	- Use bracket notation `[]` to access a property using the value of a variable. No quotes around the variable name, of course. 
	- Properties can be added just as they are modified, by assigning something to them. 
	- Delete properties using `delete`.
		- `delete myObj.prop;`

## Syntax

### Ternary operator

[Learn ReactJS: Part I - Codecademy](https://www.codecademy.com/courses/react-101/lessons/react-jsx-advanced/exercises/jsx-conditionals-ternary):

Recall how it works: you write `x ? y : z`, where `x`, `y`, and `z` are all JavaScript expressions. When your code is executed, `x` is evaluated as either “truthy” or “falsy.” If `x` is truthy, then the entire ternary operator returns `y`. If `x` is falsy, then the entire ternary operator returns `z`. 

[How do you use the ? : (conditional) operator in JavaScript? - Stack Overflow](https://stackoverflow.com/questions/6259982/how-do-you-use-the-conditional-operator-in-javascript)

### Accessing object properties with square bracket notation

[Working with objects - JavaScript - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)

An object property name can be any valid JavaScript string, or anything that can be converted to a string, including the empty string. However, any property name that is not a valid JavaScript identifier (for example, a property name that has a space or a hyphen, or that starts with a number) can only be accessed using the square bracket notation. This notation is also very useful when property names are to be dynamically determined (when the property name is not determined until runtime). 

```jsx
// four variables are created and assigned in a single go, 
// separated by commas
var myObj = new Object(),
    str = 'myString',
    rand = Math.random(),
    obj = new Object();

myObj.type              = 'Dot syntax';
myObj['date created']   = 'String with space';
myObj[str]              = 'String value';
myObj[rand]             = 'Random Number';
myObj[obj]              = 'Object';
myObj['']               = 'Even an empty string';

console.log(myObj);
```

```jsx
{type: "Dot syntax", date created: "String with space", myString: "String value", 0.00628683719320744: "Random Number", [object Object]: "Object", …}
"": "Even an empty string"
0.00628683719320744: "Random Number"
[object Object]: "Object"
date created: "String with space"
myString: "String value"
type: "Dot syntax"
__proto__: Object
```

Please note that all keys in the square bracket notation are converted to string unless they're Symbols, since JavaScript object property names (keys) can only be strings or Symbols (at some point, private names will also be added as the class fields proposal progresses, but you won't use them with `[]` form). For example, in the above code, when the key `obj` is added to the `myObj`, JavaScript will call the `obj.toString()` method, and use this result string as the new key.

## Misc

### Modules in JavaScript

React uses ES6 modules: [ES6 In Depth: Modules - Mozilla Hacks - the Web developer blog](https://hacks.mozilla.org/2015/08/es6-in-depth-modules/)

#### Import

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import { NavBar } from './NavBar.js'
```

Why the parens around `NavBar`? Because this is a "named export" and not a "single default export". See [16. Modules](https://exploringjs.com/es6/ch_modules.html#sec_overview-modules)

#### Export

The file we're importing from has to first export something.

### Getter Method

?

### `this`

[Gentle Explanation of "this" in JavaScript](https://dmitripavlutin.com/gentle-explanation-of-this-in-javascript/)

[Use this in a Component - Learn ReactJS: Part I - Codecademy](https://www.codecademy.com/courses/react-101/lessons/react-components-advanced-jsx/exercises/components-and-this)

### `.map()`

Takes an array and a function, returns a new array after running that function on each item.

The function can be passed an item and it's index.

This is useful in [React](https://www.notion.so/ranh/React-2d91d7cc23d54c93817b5cda36f9a19a#0bacddf9bf9f4e19bb71efe0f4d77aef)

[Array.prototype.map() - JavaScript - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

[Learn ReactJS: Part I - Codecademy](https://www.codecademy.com/courses/react-101/lessons/react-jsx-advanced/exercises/jsx-map)

### Creating new elements

```jsx
// Create new item for list
const li = document.createElement('li');
li.innerHTML = document.querySelector('#task').value;
```

```jsx
// Prepare the new element and add the task to it
const newTask = prompt("What to do?")
const newTaskEl = document.createElement('li')
newTaskEl.innerHTML = `${newTask} <span class="delete">X</span>`
```
