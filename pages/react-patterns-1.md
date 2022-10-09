---
title: React Patterns
---

After learning React for a few weeks, some key patterns to use for building apps. 

## Starting

React by itself doesn't make a complete application, so we use it as part of a bigger system. We still call it a "React App" beacuse...(?) React does the UI which may be the core of the app. And many of the other tools mentioned can be more or less transparent. 

This is roughly what a bigger system might look like and where React fits in:

- Tools are desinged to be used in a terminal environment. Expand...
- React is available through [npm][0001], as well as other needed tools. npm is a company that runs a free JavaScript pacakge library and offers a free tool, also called `npm`, to access it. A "package" [essentially](https://docs.npmjs.com/about-packages-and-modules) is a directory that includes a `package.json` file. In practice, npm packages are usually JavaScript code and related files that can be added to a project as drop-in _Modules_. npm is owned by GitHub which is owned by Microsoft. 
- React code gets compiled before running on the client. Babel is a JavaScript compiler that compiles [JSX](https://reactjs.org/docs/react-without-jsx.html) to standard JavaScript, and compiles some of the [JavaScript ES6](https://reactjs.org/docs/react-without-es6.html) features being used into JavaScript that more clients can understand. 
- This code, as well as any other needed files, gets _Bundled_, for example by [webpack](https://webpack.js.org/). This part integrates all the different _Modules_ into one app, and also includes things like preprocessing, minification, and any other preparation step. webpack also has a development server with live reloading. 

Building this way is generally referred to as "modern". "Modern web development" is building "modern web apps" with "modern tools" or a modern "toolchain" or a modern "environment".  

- [Creating a Toolchain from Scratch - Create a New React App – React](https://reactjs.org/docs/create-a-new-react-app.html#creating-a-toolchain-from-scratch)
- [Creating a React App… From Scratch. - Noteworthy - The Journal Blog](https://blog.usejournal.com/creating-a-react-app-from-scratch-f3c693b84658)
- [Create a New React App – React](https://reactjs.org/docs/create-a-new-react-app.html)
- [nitishdayal/cra_closer_look: An explanation of the problems that Create-React-App addresses, and how it attempts to solve them.](https://github.com/nitishdayal/cra_closer_look)
- [Building a JavaScript Development Environment - Pluralsight](https://www.pluralsight.com/courses/javascript-development-environment)
- [Build a JavaScript Dev Environment in One hour](https://www.infoq.com/presentations/javascript-dev-environment/)
- [coryhouse/javascript-development-environment: JavaScript development environment discussed in "Building a JavaScript Development Environment" on Pluralsight](https://github.com/coryhouse/javascript-development-environment)

[0001]: https://www.npmjs.com/

## React Components

A React Component is a function that takes a `props` object and returns a JSX expression. Components should be reuseable. Small Components that are responsible for one thing are more reuseable. Components can be defined as functions or classes. Initially, only components defined as classes could use certain React features such as state. In recent versions, functional components have become more powerful. It is common practice to name classes in UpperCamelCase (unlike camelCase.) 

A Component defined as a class must have a `render()` method, which must `return` something. The render function can also have code before the `return` statement.

- [Classes - JavaScript - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
- [ES6 In Depth: Classes - Mozilla Hacks - the Web developer blog](https://hacks.mozilla.org/2015/07/es6-in-depth-classes/)
- [ES6 In Depth: Subclassing - Mozilla Hacks - the Web developer blog](https://hacks.mozilla.org/2015/08/es6-in-depth-subclassing/)
- [15. Classes](https://exploringjs.com/es6/ch_classes.html)


## Listing elements with `.map()`

Given an array of (anything), we can render it in JSX using the `.map()` function. Given an array and a function, it will run the function on every  on the array, and return a new array with the results. The function we'll give to  `.map()` is like a JSX template that grabs values from the current element and fills them into a JSX expression. 


```jsx
const people = ['Rowe', 'Prevost', 'Gare'];

const peopleLis = people.map((person, i) =>
<li key={'person_' + i}>{person}</li>
);
```
[example from Codecademy](https://www.codecademy.com/courses/react-101/lessons/react-jsx-advanced/exercises/jsx-keys)
{: .cite}

```jsx
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li key={number.toString()}>
    {number}
  </li>
);
```
[example from React docs](https://reactjs.org/docs/lists-and-keys.html#keys)
{: .cite}

`.map()` takes one argument, which is a function, but that function can take four arguments. Here we're using the first two. The first paramater, `currentValue`, is given the argument `person`, so `person` will be the variable we use inside the function to refer to the value of the current element being processed in the array. The second is `index`, and we're giving it `i`, so `i` will be the variable we can use inside the function to refer to the index of the current element. 

The index will be a unique value for each element in the array, so we can use it to assign unique keys to every JSX element we create. React will complain if we don't add unique keys. According to the docs, "Keys should be given to the elements inside the array to give the elements a stable identity".


- [Lists and Keys – React](https://reactjs.org/docs/lists-and-keys.html)
- [Array.prototype.map() - JavaScript - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

## State with Hooks
 
Hooks are a relatively late addition to React. They bring state to functional components. Previously state was only available for classes. This should make it easier to develop with React, becuause it avoids the issues related to classes. Expand...

## Basic interactions 