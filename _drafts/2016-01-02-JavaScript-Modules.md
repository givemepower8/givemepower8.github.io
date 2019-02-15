# JavaScript Module

Modules help to

- organize the codebase physically and logically
  - namespacing, global namespace can be easily polluted
  - separate functionality
  - quickly locate files
- reuseable code
  - module enables thousands of npm packages
- maintainable code
  - lessen the dependencies
- bundled package
  - specify dependencies
  - increase page load speed

How to use a module

- export
- import
- build and bundle

[basics-of-modular-javascript](https://medium.com/@crohacz_86666/basics-of-modular-javascript-2395c82dd93a)

[Everything I know about writing modular JavaScript applications](https://medium.com/dev-bits/everything-i-know-about-writing-modular-javascript-applications-37c125d8eddf)

[CommonJS vs AMD vs RequireJS vs ES6 Modules](https://medium.com/computed-comparisons/commonjs-vs-amd-vs-requirejs-vs-es6-modules-2e814b114a0b)

[modules eloquent javascript](https://eloquentjavascript.net/10_modules.html)

[Book - Mastering Modular JavaScript](https://www.oreilly.com/library/view/mastering-modular-javascript/9781491955673/)

[mjavascript](https://mjavascript.com/)

[when-should-i-use-curly-braces-for-es6-import](https://stackoverflow.com/questions/36795819/when-should-i-use-curly-braces-for-es6-import)

[JavaScript Modules](https://jsmodules.io/cjs.html)

[How the module system, CommonJS & require works](https://blog.risingstack.com/node-js-at-scale-module-system-commonjs-require/)

There are currently 3 primary competing standards for JavaScript modules:

- AMD or Asynchronous Module Definition
- [CommonJS](https://nodejs.org/docs/latest/api/modules.html)
- EcmaScript 6 Modules

AMD modules look like this:

```js
define(['file1', 'file2'], function(Class1, Class2) {
  let obj = new Class1(),
    obj2 = new Class2();
  return obj.foo(obj2);
});
```

commonJS

```js
let Class1 = require('file1'),
  Class2 = require('file2'),
  obj = newClass1(),
  obj2 = new Class2();

module.exports = obj.foo(obj2);
```

ES6 / 2015 Modules

```js
import Class1 from 'file1';
import Class2 from 'file2';

let obj = newClass1(),
  obj2 = new Class2();

export default obj.foo(obj2);
```

## Module Loaders

Module loaders are tools for specifying dependencies for JavaScript files and loading those files into a browser.

Module loaders improve on that by allowing you to define dependencies for your JavaScript files, and assuring that those dependencies are loaded in the correct order so that the variables the code needs are there when referenced.

These dependencies are specified using one of several "module formats".

### Module Formats (AMD, RequireJS) / (CommonJS, Node) / (ES6 / 2015, SystemJS)

- AMD Format (Asynchronous Module Definition)
  Primarily used for JavaScript modules that need to be included in a browser as opposed to server side JavaScript
- CommonJS Format
  Primarily used in server side implementations as part of NodeJS applications
- ES6 / 2015 format
  ES6 added support for modules. Although ES6 has some cool new features, a lot of these features are not compatible with most modern day web browsers.

## ES6 / 2015 Module

With the advent of modules in ES2015, we now don't need to use any third party libraries to create modular JavaScript code. Unfortunately, modern day browsers don’t support ES2015 code quite yet, which means our user’s browsers cannot render the code we write in the newest version of JS. The solution to this has been transpilers.

### export statement

[export statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)

### import statement

[import statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)

### SystemJS

SystemJS is a module loader more lightweight, because Angular 2 components are written in TypeScript, and ES6, so you need a loader to import these files.

[SystemJS on github](https://github.com/systemjs/systemjs)

[Modular JavaScript: A Beginners Guide to SystemJS & jspm](https://www.sitepoint.com/modular-javascript-systemjs-jspm/)

## AMD and RequireJS

RequireJS is one of the most popular loaders.

[Moving Past RequireJS](https://benmccormick.org/2015/05/28/moving-past-requirejs)

RequireJS requires developers to use AMD modules. That choice made a ton of sense in 2011 when RequireJS first launched. It makes less sense today. In 2011, the only popular alternative to AMD modules was the CommonJS standard, and AMD held a technical advantage over CommonJS. It was essentially a decision between a technological superiority and a cleaner API. In 2015, AMD is one of 3 realistic module syntax alternatives, and no longer holds a significant technical advantage, but it still has a less clear syntax and has begun to experience problems with network effects.

In 2015, RequireJS is one of 3 major options on the module loading scene, along with Browserify and Webpack. Browserify is an attempt to build a module loader on top of the NPM ecosystem and node modules. It uses CommonJS modules and integrates tightly with NPM. Webpack is an attempt to unify the modules landscape by supporting AMD, CommonJS and ES6 modules. It handles JavaScript, CSS and other assets, as well as preprocessors for each. RequireJS suffers in comparison to both of them, both in terms of features and workflow.

[Why AMD](https://requirejs.org/docs/whyamd.html)

## CommonJS and Node
