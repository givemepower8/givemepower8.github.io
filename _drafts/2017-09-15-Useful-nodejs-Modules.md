# Useful packages

## browserify

Browserify lets you require('modules') in the browser by bundling up all of your dependencies.

[Official](http://browserify.org/)
[browserify on github](https://github.com/browserify/browserify)
[browserify-handbook](https://github.com/browserify/browserify-handbook)

### options

--debug

### tsify

Browserify plugin for compiling TypeScript.

[tsify](https://www.npmjs.com/package/tsify)

```js
var browserify = require("browserify");
var tsify = require("tsify");

browserify()
  .add("main.ts")
  .plugin(tsify, { noImplicitAny: true })
  .bundle()
  .on("error", function(error) {
    console.error(error.toString());
  })
  .pipe(process.stdout);
```

### watchify

Watch mode for browserify builds.

[watchify](https://github.com/browserify/watchify)

### beefy

A local development server that aims to make writing modular client-side apps with NPM + browserify fast and fun.

## http-server

[http-server](https://www.npmjs.com/package/http-server)

`npm install http-server -g`

Uninstall lite-server if installed

`npm uninstall lite-server`

`npm uninstall lite-server -g`

[serve](https://www.npmjs.com/package/serve)
