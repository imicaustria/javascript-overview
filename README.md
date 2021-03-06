# JavaScript Cheatsheet

:exclamation::hand: **NOTE: THIS DOCUMENT IS CURRENTLY UNDER DEVELOPMENT** :hand::exclamation:

Here we will keep an ongoing list of the logic and code we explore/review in class, categorized by topic.

- [JavaScript Cheatsheet](#javascript-cheatsheet)
  - [Miscellaneous](#miscellaneous)
  - [Data types](#data-types)
  - [Arithmetic operators](#arithmetic-operators)
  - [Variables](#variables)
  - [Template literals](#template-literals)
  - [Functions](#functions)
    - [Arrow Functions](#arrow-functions)
  - [Object (literal)](#object-literal)
  - [Array](#array)
  - [Conditions](#conditions)
    - [Comparison operators](#comparison-operators)
  - [Loops](#loops)
  - [Utility Libraries](#utility-libraries)
    - [Math library](#math-library)
  - [Document (DOM)](#document-dom)
    - [Nodes](#nodes)
    - [Select a single Element](#select-a-single-element)
    - [Selecting multiple elements at once](#selecting-multiple-elements-at-once)
    - [Common element properties](#common-element-properties)
    - [Physical dimensions of an Element](#physical-dimensions-of-an-element)
  - [Event listeners](#event-listeners)
  - [Creating elements](#creating-elements)
  - [Window (and document)](#window-and-document)
    - [Dimensions](#dimensions)
    - [Window scrolling](#window-scrolling)
    - [Window Events](#window-events)
  - [Timers](#timers)
    - [Window framerate timer](#window-framerate-timer)


## Miscellaneous
- Single-line comments: `// comment!`
- Multi-line comments: `/* comment! */`
- Browser "console" testing messages: `console.log('hello world')`

[Read more on miscellaneous JavaScript tidbits](./01-javascript/)


## Data types
In Javascript there are *eight* data types (seven "primitive" data types, plus `Object` - more on that later). The three primitive types that are most recognizable to beginners are: `Number`, `String` and `Boolean`:

```javascript
12345.67       // Number (integer, decimal, positive or negative)
'Hello world'  // String ('', "", or ``)
true           // Boolean (true or false)
```

[Read more on data types](./02-data-types/)


## Arithmetic operators
Will perform some mathematical operation with numbers
```javascript
5 + 2        // 7
5 - 2        // 3
5 * 2        // 10
5 / 2        // 2.5
5 ** 2       // 25 (exponent)
5 % 2        // 1 (remainder, aka "modulus")
5 + 2 * 3    // 11
(5 + 2) * 3  // 21 (BEDMAS/PEDMAS!)
```

[Read more on operators](./03-operators/)


## Variables
Variables hold a single value. Use `var`, `let` or `const` (constant: can not later be changed) to declare a variable the first time. Use `=` ("assignment operator") to assign a value to a variable.

```javascript
let name
name = 'Ada Lovelace'
```

[Read more on variables](./04-variables/)


## Template literals

String surrounded by back-ticks (`` ` ``) can contain expressions within it by using the evaluator symbol: `${ }`

```javascript
let name = 'Alan Turing'
`Hey ${name}, can machines think?`  // Hey, Alan Turing, can machines think?
```

[Read more on template literals](./05-template-literals/)


## Functions

An executable block of procedural code that can exclusively perform actions and/or return a single value to the point in code from which the function was called. Functions can receive instructions ("arguments") meant to modify its behaviour.

```javascript
function greetings(name) {
  return `Hello, ${name}!`
}
```

Call a function by using its name and passing it the desired arguments:

```javascript
greetings(`Brendan Eich`)   // Hello, Brendan Eich!
greetings(`Grace Hopper`)   // Hello, Grace Hopper!
```

Here, the string that passed is assigned to `name` in the function named `greetings`

### Arrow Functions
The same function above can be written using `=>` notation ("fat arrow", or "lamba"):

```javascript
const greetings = (name) => {
  return `Hello, ${name}!`
}
```

Arrow functions can be called the same way as standard functions.

[Read more on functions](./06-functions/)


## Object (literal)

Objects (in this case, referred to as "Object literals") allow multiple values (known as "properties") to be stored in a single structure.

```javascript
const person = {
  name: 'Dorothy Vaughan', 
  occupation: 'Human Computer'
}
```

The variable an Object is assigned to is actually holding a _reference_ to the Object, not the Object itself.

[Read more on object literals](./07-object-literals/)


## Array

Arrays, like Object literals, allow multiple values to be stored in a single structure. However, array values are indexed, rather than named.

```javascript
const hiddenFigures = [
  'Dorothy Vaughan', 
  'Katherine G. Johnson',
  'Mary Jackson'
]
```

As with Objects, the variable that Arrays are assigned to, hold a _reference_ to the Array, not the Array itself.

[Read more on arrays](./08-arrays/)


## Conditions

A condition can be checked using an `if` statement. If the "condition" is `true`, the block will run, if `false` (or "falsy") it will evaluate the next condition (if one exists).

```javascript
if ( condition ) {
  // the initial condition
} else if ( condition ) {
  // (optional) condition(s) can be added after the initial "if"
} else {
  // (optional) "default" condition
}
```

### Comparison operators

*Comparison operators* are binary operators that compare their left and right value or variable, resulting in a `Booleans` (`true` or `false`): 
- `==` (equal value), `!=` (not equal to), `<` (less than), `>` (greater than), `<=` (less than or equal to), `>=` (greater than or equal to)
- Comparing both value _and_ type: `===` (equal in value and type), `!==` (not equal in type or value)

Other condition evaluation techniques: ternary, case/switch statements

[Read more on conditions](./09-conditions/)


## Loops

Coming soon: for, for...in, while, and more.

[Read more on arrays](./10-loops/)


## Utility Libraries

### Math library

A few useful `Math` functions:

```javascript
Math.random()    // a random number between 0 and 0.999
Math.round(5.5)  // 6, because of standard rounding rules
Math.ceil(5.5)   // 6, ceil (ceiling) always rounds up
Math.floor(5.5)  // 5, floor always rounds down
```

[Read more on utility libraries](./11-libraries/)


## Document (DOM)
Refer to the entire live browser page with: `document`. From there, you can search for elements that exist and manipulate them. 

- `document`: represents the entire physical interface and all of it's functionality and parts
- `document.documentElement`: The top level container (the `<html>` Element)
- `document.body`: The container that holds the physical interface (the `<body>` Element)

### Nodes

[`Element`](https://developer.mozilla.org/en-US/docs/Web/API/Element) and the [`Document`](https://developer.mozilla.org/en-US/docs/Web/API/Document) are both technically a (subtype of) [`Node`](https://developer.mozilla.org/en-US/docs/Web/API/Node). Other `Node` subtypes are `Comment` and `Text`. A good [visual explanation of Node types in an HTML document can be found here](https://javascript.info/dom-nodes#an-example-of-the-dom).


### Select a single Element

```javascript
document.getElementById('submitBtn')  // Finds the HTML element with id="submitBtn"
document.querySelector('.btn')  // Finds only the *first* HTML element with class="btn"
```

Returns a reference to the first matching Element found, or `null` if a match is not found. Element references can be stored into variables for recall.


### Selecting multiple elements at once
```javascript
document.querySelectorAll('.btn')  // Finds *all* HTML elements with class="btn"
```
Will store the found Element references in an array-like structure. To work with the resulting elements, iterate over them using a loop, just as you would an Array:

```javascript
const allButtons = document.querySelectorAll('.btn')  // Select all ".btn" elements

allButtons.forEach(aBtn => {
  // Each ".btn" Element is now referred to as "aBtn" one-by-one because we declared it so in this function definition (above)
})
```

### Common element properties

Each elements in a document (an Object of type `Element` in JavaScript) has specific properties and methods defined that allows it to be modified at any time, in real time. 

For example, given an element (HTML) structured as such: `<h1 class="heading"></h1>`. After selecting the element (store the reference as `ele`), here are a few properties or methods to perform common actions.

```javascript
const ele = document.querySelector('.test')  // Select an element, store the reference

// Modify the content between the opening/closing tags (treat HTML as text)
ele.textContent = `Hello, world!`

// Modify the content between the opening/closing tags, to include HTML
ele.innerHTML = `Hello, <strong>world</strong>!`

// Modify a single CSS property, like "color" and "text-align"
ele.style.color = `tomato`
ele.style.textAlign = `right`

// Affect the classes applied to an element
ele.classList.add(`highlight`)
ele.classList.remove(`highlight`)
ele.classList.toggle(`highlight`)

// HTML element attributes (get and set)
ele.setAttribute(`title`, `Hello world`)  // Modify/add an attribute (title="Hello world")
ele.getAttribute(`title`)  // Returns the String: Hello world
```


### Physical dimensions of an Element

```javascript
const ele = document.querySelector('.test')  // Select an element, store the reference

// px sizes of content including padding and border
ele.offsetWidth
ele.offsetHeight

// px sizes of content including padding (but not border)
ele.clientWidth
ele.clientHeight

// px sizes of the element as an exact decimal
ele.getBoundingClientRect().height
ele.getBoundingClientRect().width

// px measurements to an element relative to the document
ele.offsetTop
ele.offsetRight
ele.offsetBottom
ele.offsetLeft

// px measurement (decimal) relative to the window (viewport)
ele.getBoundingClientRect().top
ele.getBoundingClientRect().right
ele.getBoundingClientRect().bottom
ele.getBoundingClientRect().left
```


[Read more on the document (object model)](./12-document/)


## Event listeners
Replace `ele` with a reference to the element you want to make clickable, and place the code to execute (on occurrence of the event) between the `{ }` callback (or "handler").

```javascript
ele.addEventListener('click', event => {  })
```
A list of [some comment Event types can be found here](https://developer.mozilla.org/en-US/docs/Web/Events).

[Read more on events](./13-events/)


## Creating elements

Info on `insertAdjacent`, `innerHTML` and `createElement` coming soon.

[Read more on creating elements [coming soon]](./)


## Window (and document)

The browser is referred to as the `window`. The window holds the `document.documentElement` (aka, the `<html>` element). 

In addition to controlling the browser's `history` and `console` (amongst other key components), the `window` (and the `documentElement`) can be used to help with interaction by using some of its key properties or methods:

### Dimensions

```javascript
let $doc = document.documentElement  // Select the <html> element (the biggest wrapper there is)

// Window, including scrolls bars (window's outside perimeter)
let windowHsc = window.innerHeight  // window height (px)
let windowWsc = window.innerWidth  // window width (px) 

// Window, not including scrolls bars (inside of the scroll bars)
let windowH = $doc.clientHeight  // window height (px)
let windowW = $doc.clientWidth  // window width (px)
// ** this is weird one! it's obtaining the windows true inner dimensions via the documentElement

// Dimensions of any element (including content and padding, but not border or margin)
let documentH = $doc.scrollHeight
let documentW = $doc.scrollWidth
```

### Window scrolling

```javascript
// Get the current window scroll position (px)
let scrollPxVert = window.scrollY
let scrollPxHorz = window.scrollX

// Scroll to an element
ele.scrollIntoView()  // hard scroll the window
ele.scrollIntoView({ behavior:'smooth' })  // soft scroll the window

// Scroll to a coordinate in the document
window.scrollTo(0, 0)  // hard scroll the window (x, y)
window.scrollTo({ left:0, top:0, behavior:'smooth' })  // soft scroll the window
```


### Window Events

A few common window events are: `'load'`, `'scroll'`, `'resize'`, `'hashchange'`


[Read more on the window [coming soon]](./)


## Timers

### Window framerate timer

```javascript
// use the browser's animation framerate to do something over and over again
let count = 0;  // optional counter

// Function to run over and over (call it whatever you want)
const loop = () => {

  // Check a condition (here, a max number of times it should run: 10)
  // If the limit was hit, escape immediately
  if (++count > 10) return   // "return" quits the function

  // Do whatever the actions is
  console.log(`Iteration number: ${count}`)

  // Loop again if we got this far!
  window.requestAnimationFrame(loop)
}

// Start looping!
window.requestAnimationFrame(loop)
```


Coming soon: setInterval/clearInterval, setTimeout/clearTimeout, requestAnimationFrame/cancelAnimationFrame

[Read more on timers [coming soon]](./)






