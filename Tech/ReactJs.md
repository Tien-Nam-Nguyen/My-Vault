---
type:
  - Tech
tags:
  - ReactJS
  - Javascript
  - Frontend
  - Library
published: true
folder: Tech
---
# What is React?

React is a library for developing front-end using Javascript. It uses components (usually functional components) that looks like html to embed it into Javascript code. Those components are implemented in .jsx file.

Npm (node package manager) and yarn are some popular package manager for react and others Javascript library. All you do is just install Nodejs.

# Directory structure

- node_modules: contains external library that you have installed through package manager.
- public: contains public assets url(e.g. fonts, images, ...)
- src: contains source code
- package.json: contains metadata about your projects
- package-lock.json: like package.json but ensure the version of the packages.
- index.html: main html entry of the project
- index.css: main css entry of the project

# DOM

DOM (Document Object Model) is a representation of the HTML elements in the browser as a tree structure. Each element in the DOM is treated as an object, allowing us to access and manipulate those elements using Javascript.

Whenever the state of the app changes, React updates the DOM. However, directly updating DOM can lead to poor performance due to the process of re-rendering the entire DOM .

# Virtual DOM

Virtual DOM is an optimization mechanism that React uses to manage and update the DOM. It is a lightweight DOM.

When a state of the app changes, React create a new Virtual DOM tree based on component structure and the new state. Then, React compare this new tree with previous tree. The differences are determined, and React only updates the actual DOM for the changed elements, instead of updating the entire DOM


# Props

Props is like a object parameter of a functional component. One component can only have one props parameter.

# React hook

React hook are some special function that allows **functional components** to use React features without writing class components like before (React v16.8). React hook are started with "use" word (e.g. useState, useEffect, useReducer, useContext, ...)
## useState

It is a hook that allows the creation of a stateful variable and a setter function to update its value in the Virtual DOM.

```javascript
const [val, setVal] = useState(0);
```

## useEffect

It is a hook that tells React to execute some code when (pick one): 
- This component re-renders
- This component mounts
- The state of some values change

```javascript
useEffect(() => {})              // Runs after every re-render
useEffect(() => {}, [])          // Runs only on mount
useEffect(() => {}, [value])     // Runs on mount + when value changes
```

It should be used in following situations:
- Event listeners
- DOM manipulation
- Subscriptions (real-time updates)
- Fetching data from an API
- Clean up when a component unmounts

## useContext

It is a hook that allows you to share values between multiple levels of components without passsing props through each level

## useRef

It is a hook that does not re-renders when its value changes. When you want a component to "remember" some information, but you don't want that information to trigger new renders.

It should be used in following situations:
- Accessing/Interacting with DOM elements
- Handling Focus, Animations and Transitions
- Managing Timers and Intervals

```javascript
const ref = useRef(0);
```







