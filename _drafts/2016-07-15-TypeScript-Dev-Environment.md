# TypeScript Environment

## VS Code Dev Environment

TypeScript development work is supported in VS Code.

[setting-up-your-typescript-vs-code-development-environment](http://blog.wolksoftware.com/setting-up-your-typescript-vs-code-development-environment)

Install globally
`npm install -g typescript`

Install locally
`npm install –save-dev typescript`

`npm list -g typescript`

`npm list typescript`

Update
`npm update -g typescript@latest`

## tsc Compiler

tsc is the typescript compiler which compiles .ts file to .js file
To check where tsc is installed
`where tsc`

`tsc -v`

[tsc command](https://www.typescriptlang.org/docs/handbook/compiler-options.html)

### Watch

[tsc -w](https://stackoverflow.com/questions/12799237/how-to-watch-and-compile-all-typescript-sources)
Open a terminal and run tsc -w, it'll compile any .ts file in src directory into .js and store them in ts-built directory.

### tsconfig.json

`tsc --init`
to create [tsconfig.json](http://www.typescriptlang.org/docs/handbook/tsconfig-json.html) file

Sample

```js
{
    "compilerOptions": {
        "experimentalDecorators": true,
        "emitDecoratorMetadata": true,
        "module": "commonjs",
        "target": "ES5",
        "outDir": "ts-built",
        "rootDir": "src"
    }
}
```

[tsconfig.json](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/tsconfig.json.md)

[configuring-typescript-compiler](https://blog.angularindepth.com/configuring-typescript-compiler-a84ed8f87e3)

### compilerOptions

"sourceMap": true,
"target": "ES2015",
Typescript is compiled into ECMAScript. You can specify the target version of ECMAScript.

#### module

[JavaScript Module Systems Showdown: CommonJS vs AMD vs ES2015](https://auth0.com/blog/javascript-module-systems-showdown/)

[CommonJS vs AMD vs RequireJS vs ES6 Modules](https://medium.com/computed-comparisons/commonjs-vs-amd-vs-requirejs-vs-es6-modules-2e814b114a0b)

[tsconfig](https://basarat.gitbooks.io/typescript/docs/project/tsconfig.html)

## Test-driven

[An Overview of JavaScript Testing in 2018](https://medium.com/welldone-software/an-overview-of-javascript-testing-in-2018-f68950900bc3)

### mocha and gulp-mocha

[run-typescript-mocha-tests-in-visual-studio-code](https://medium.com/@FizzyInTheHall/run-typescript-mocha-tests-in-visual-studio-code-58e62a173575)
[mocha-test-runner-with-gulp](https://gulpjs.org/recipes/mocha-test-runner-with-gulp.html)
[Write tests for TypeScript projects with mocha and chai — in TypeScript!](https://journal.artfuldev.com/write-tests-for-typescript-projects-with-mocha-and-chai-in-typescript-86e053bdb2b6)

[gulp-mocha](https://www.npmjs.com/package/gulp-mocha)
[mocha-typescript](https://www.npmjs.com/package/mocha-typescript)
[Using Istanbul With TypeScript & mocha](https://istanbul.js.org/docs/tutorials/typescript/)

### Jest, ts-jest

[Debugging with TypeScript, Jest, ts-jest and Visual Studio Code](https://medium.com/@mtiller/debugging-with-typescript-jest-ts-jest-and-visual-studio-code-ef9ca8644132)

[ts-jest](https://github.com/kulshekhar/ts-jest)

### Test automation

[Unit testing node applications with TypeScript — using mocha and chai](https://journal.artfuldev.com/unit-testing-node-applications-with-typescript-using-mocha-and-chai-384ef05f32b2)

[Writing unit tests in TypeScript](https://medium.com/@RupaniChirag/writing-unit-tests-in-typescript-d4719b8a0a40)

[istanbul.js/](https://istanbul.js.org/)

## Continuous Integration

### Build automation

The common steps are:

1. compile all the ts files into to js files
2. jslint the js files
3. uglify the js files
4. bundle all the js files into one bundle.js

```js
var gulp = require("gulp");
var ts = require("gulp-typescript");

gulp.task("default", function() {
  var tsResult = gulp.src("src/*.ts").pipe(
    ts({
      noImplicitAny: true,
      out: "output.js"
    })
  );
  return tsResult.js.pipe(gulp.dest("built/local"));
});
```

## Useful packages

### DefinitelyTyped @types/[package]

Starting from TypeScript 2.0, users can install typings using npm install @types/[package]. These typings are coming from [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)

`npm install @types/node --save-dev`

### tslint

TSLint is an extensible static analysis tool that checks TypeScript code for readability, maintainability, and functionality errors.

`npm install -g tslint`

[tslint on github](https://github.com/palantir/tslint)

```js
gulp.task("lint", function() {
  return gulp
    .src(["src/**/**.ts", "test/**/**.test.ts"])
    .pipe(tslint({}))
    .pipe(tslint.report("verbose"));
});
```

### typedoc

[typedoc](https://github.com/TypeStrong/typedoc)

### ts-node

TypeScript execution and REPL for node.js, with source map support.
[ts-node](https://www.npmjs.com/package/ts-node)
[ts-node on github](https://github.com/TypeStrong/ts-node)

Install
`npm install -g ts-node`
`npm install -g typescript`

To launch ts-node, run the following:
`ts-node`

## Resources

[Official](https://www.typescriptlang.org/index.html)

[GitHub Source Code](https://github.com/Microsoft/TypeScript)

[TypeScript Doc](http://www.typescriptlang.org/docs/home.html)

[Samples](http://www.typescriptlang.org/samples/)

[GitHub handbook](https://github.com/Microsoft/TypeScript-Handbook)

[Spec](https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md)

[Online books](https://basarat.gitbooks.io/typescript/)

[pluralsight - beyond asp.net web development demystified](https://app.pluralsight.com/library/courses/beyond-aspdotnet-web-development-demystified/)

[pluralsight- javascript development environment](https://app.pluralsight.com/library/courses/javascript-development-environment/)
