---
layout: post
title: Learn TypeScript
subtitle: Learn TypeScript
date: 2016-07-01 16:16:01 -0800
categories: [TypeScript]
tags: [TypeScript]
---

# TypeScript language

Lots of language features are already included in ECMA script.

## Variable

[Basic Types](http://www.typescriptlang.org/docs/handbook/basic-types.html)

- bool
- number
- string
- array
- tuple
- enum
- any
- void
- null and undefined
- never
- object

Void still returns undefined.
Never is often used in error handling.

[symbols](http://www.typescriptlang.org/docs/handbook/symbols.html)

### Declaration

#### Scope

let, const, var
[variable-declarations](http://www.typescriptlang.org/docs/handbook/variable-declarations.html)

#### Ambient Declaration

[ambient declaration](https://basarat.gitbooks.io/typescript/docs/types/ambient/intro.html)

[typescript_ambients](https://www.tutorialspoint.com/typescript/typescript_ambients.htm)

[typescript-ambient-declarations](https://medium.com/@mikenorth/guide-to-typescript-ambient-declarations-717ef6da6514)

## Array / Collection

Iterators

Generators
[Generator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator)

[GeneratorFunction](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/GeneratorFunction)

[iterators-and-generators](http://www.typescriptlang.org/docs/handbook/iterators-and-generators.html)

## Functions

[functions](http://www.typescriptlang.org/docs/handbook/functions.html)

### Invokation

Immediately Invoked Function Expression (IIFE).

```js
var a = 2;

(function IIFE() {
  var a = 3;
  console.log(a); // 3
})();

console.log(a); // 2
```

### Parameters

Positional Parameters
Default values

Optional Parameters

#### Spread / Rest parameter

... is spread / rest parameter.

### Return type

void

### Overloading

### Arrow functions (Lambda)

## Object oriented

### Interface

[interfaces](http://www.typescriptlang.org/docs/handbook/interfaces.html)

Structure (duck) typing

### Class

[classes](http://www.typescriptlang.org/docs/handbook/classes.html)

Members

Constructor

Abstract class

this

#### Static class

Cannot create instances.

Static members

#### Variance

- Covariance accepts super/ base type but not sub types. out
- Contravariance accepts the type and subtypes but not super/base types. in
- Bivariance accepts both of the above.

Override and super

### Decorators

[decorators](http://www.typescriptlang.org/docs/handbook/decorators.html)

TypeScript decorators can be set on different targets:

- class
- property
- accessor
- method
- parameter

It’s kind of like the attributes in .net.

### Mixins

[Mixins](http://www.typescriptlang.org/docs/handbook/mixins.html)

## Typing

[Type Inference](http://www.typescriptlang.org/docs/handbook/type-inference.html)

[type compatibility](http://www.typescriptlang.org/docs/handbook/type-compatibility.html)

### Generics

[generics](http://www.typescriptlang.org/docs/handbook/generics.html)

[advanced-types](http://www.typescriptlang.org/docs/handbook/advanced-types.html)

### Type checking

[type-checking](http://www.typescriptlang.org/docs/handbook/type-checking-javascript-files.html)

## Modules

[modules](https://www.typescriptlang.org/docs/handbook/modules.html)

[module-resolution](http://www.typescriptlang.org/docs/handbook/module-resolution.html)

[packaging](https://itnext.io/step-by-step-building-and-publishing-an-npm-typescript-package-44fe7164964c)

[JavaScript module](https://app.pluralsight.com/library/courses/javascript-module-fundamentals/)

Namespace and export

Import

### namespace

[namespaces](http://www.typescriptlang.org/docs/handbook/namespaces.html)

[namespaces-and-modules](http://www.typescriptlang.org/docs/handbook/namespaces-and-modules.html)

[declaration-merging](http://www.typescriptlang.org/docs/handbook/declaration-merging.html)

### Declaration files

[declaration-files](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)

.d.ts

## Resources

[TypeScript-Handbook](https://github.com/Microsoft/TypeScript-Handbook)

[learn typescript](https://github.com/TypeStrong/learn-typescript)
