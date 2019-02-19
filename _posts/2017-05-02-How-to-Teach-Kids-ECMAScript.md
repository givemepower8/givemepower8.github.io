---
layout: post
title: How to Teach Kids ECMAScript
subtitle: How to Teach Kids ECMAScript
date: 2017-05-02 06:21:11 -0800
categories: [ECMAScript]
tags: [ECMAScript]
---

# How to Teach Kids ECMAScript

## Basics - the whole picture of the web

At the first stage, you need to help the kids get familiar with the terms and have a basic understanding of the whole picture of the web:

- HTML, assets like images
- CSS styling
- DOM elements and events
- Web server, DNS basics
- HTTP request and response
- JavaScript, ECMAScript, TypeScript
- Browser or node.js which runs ECMAScript
- Development tools like Visual Studio Code

[JavaScript Basics on MDN](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)

### Variables

[Variables](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Variables)

#### var, let, const and scope

#### Variable type

| Type                                                                                            | Description                                                                                                      |
| ----------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| [Bool](https://devdocs.io/javascript/global_objects/boolean)                                    | A True/False value. The words true and false are special keywords in JS, and don't need quotes.                  |
| [Number](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Math)            | A number. Numbers don't have quotes around them.                                                                 |
| [String](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Strings)         | A sequence of text known as a string. To signify that the value is a string, you must enclose it in quote marks. |
| [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) | A structure that allows you to store multiple values in one single reference.                                    |
| [Objects](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects)                    | Basically, anything. Everything in JavaScript is an object, and can be stored in a variable.                     |

##### Boolean

##### Numbers

[Numbers and dates](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Numbers_and_dates)

##### String

[Formatting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Text_formatting)

##### Date and time

#### Naming conventions

### Statements

[Keywords in statements](https://devdocs.io/javascript-statements/)

[Expression and operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)

#### Control flow

[Control flow](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals)

[Loops and iteration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)

### Functions

[Functions](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions)

### Array

[Array in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

#### Create an Array

The following statements create equivalent arrays:

```js
var arr = new Array(element0, element1, ..., elementN);
var arr = Array(element0, element1, ..., elementN);
var arr = [element0, element1, ..., elementN]; // recommended
```

#### index and items

Array has a length property.

Array's index is 0-based, from 0 to (array.length - 1).

Items are accessed by the index.

- Index and access items
- Change item
- Add item
  - push() - add to the end
  - unshift() - add to the front
- Remove item
  - pop() - remove from the end
  - shift() - remove from the front
  - splice() - remove by index
- Search item
  - indexOf()

#### Array iteration

for and index

forEach

slice() copy an array

### Object

[Objects](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects)

[Working with objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)

[Details of the Object Model](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Details_of_the_Object_Model)

### Troubleshooting

> “To err is human.”

Type of errors, easy-to-catch ones are typos, language syntax, variable not accessible, wrong returns.

Hard-to-catch ones are logic ones. The code compiles and works for most of the scenarios but returns wrong values for some cases.

### Error handling

## Beyond the basics

### Regex

## Environment setup

- install nodeJS
- install git
- install chrome
- install visual studio code
- get an account on GitHub
- install a static web server npm package
