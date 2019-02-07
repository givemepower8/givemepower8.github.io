---
layout: post
title:  How to use gulp
subtitle: How to use gulp
date:   2018-03-01 06:21:11 -0800
categories: [Dev Tools, Gulp]
tags: [Dev Tools, Gulp]
---
# How to use gulp

gulp is the task runner to setup and run the common tasks as following:

* clean up the deployment package folder
* compile the ts files to js files
  * bundle the js files into one file
  * uglify the js
  * minify the js file
* css files
  * sass or less
  * minify the css file
* integration
* watch for source code changes and reload
* setup html

[gulp-as-a-development-web-server](https://code.tutsplus.com/tutorials/gulp-as-a-development-web-server--cms-20903)

[gulp-browserify-starter-faq](https://www.viget.com/articles/gulp-browserify-starter-faq/)

## Installation

`npm install -g gulp`

`npm install --save-dev gulp`

To check version
`gulp -v`

## Visual Studio Code Support

## TypeScript Support

[build TypeScript with gulp](http://www.typescriptlang.org/docs/handbook/gulp.html)

## Tasks

[Fast browserify builds with watchify](https://github.com/gulpjs/gulp/blob/master/docs/recipes/fast-browserify-builds-with-watchify.md)

[gulp task recipes](https://gulpjs.org/recipes/running-tasks-in-series.html)

All tasks are maintained in gulpfile.js file

[creating-tasks](https://gulpjs.com/docs/en/getting-started/creating-tasks)

default task

```js
function defaultTask(cb) {
  // place code for your default task here
  cb();
}

exports.default = defaultTask
```

or

```js
gulp.task("default", function () {
  // place code for your default task here
});
```

### Task dependencies

## Related packages

### gulp-typescript

[gulp-typescript](https://www.npmjs.com/package/gulp-typescript)

`npm install --save-dev gulp-typescript`

### gulp-sourcemaps

[Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/)

[gulp-sourcemaps](https://www.npmjs.com/package/gulp-sourcemaps)

### gulp-connect

[gulp-connect](https://www.npmjs.com/package/gulp-connect)
[gulp-connect on github](https://github.com/AveVlad/gulp-connect)

Basic

```js
var gulp = require('gulp'),
  connect = require('gulp-connect');

gulp.task('connect', function() {
  connect.server();
});

gulp.task('default', ['connect']);
```

LiveReload

```js
var gulp = require('gulp'),
  connect = require('gulp-connect');

gulp.task('connect', function() {
  connect.server({
    root: 'app',
    livereload: true
  });
});

gulp.task('html', function () {
  gulp.src('./app/*.html')
    .pipe(gulp.dest('./app'))
    .pipe(connect.reload());
});

gulp.task('watch', function () {
  gulp.watch(['./app/*.html'], ['html']);
});

gulp.task('default', ['connect', 'watch']);
```

### gulp-mocha

`npm install --save-dev gulp-mocha`

### gulp-tslint

`npm install  --save-dev gulp-tslint`

```js
var gulp = require("gulp");
var ts = require("gulp-typescript");
var tsProject = ts.createProject("tsconfig.json");

gulp.task("default", function () {
    return tsProject.src()
        .pipe(tsProject())
        .js.pipe(gulp.dest("dist"));
});
```

### gulp-uglify

`npm install  --save-dev gulp-uglify`

### gulp-open

[gulp-open on github](https://github.com/stevelacy/gulp-open)
[Refresh-webpages-automatically-during-development-using-Gulp](http://www.codeblocq.com/2015/11/Refresh-webpages-automatically-during-development-using-Gulp/)

npm install  --save-dev browser-sync
npm install  --save-dev browserify
npm install  --save-dev chai
npm install  --save-dev gulp-istanbul
npm install  --save-dev gulp-sourcemaps

npm install  --save-dev vinyl-buffer
npm install  --save-dev vinyl-source-stream

## Resources

[gulp documentation](https://gulpjs.com/)

[gulp recipes](https://gulpjs.org/recipes/)

[gulp on medium](https://medium.com/gulpjs)

[getting started](https://semaphoreci.com/community/tutorials/getting-started-with-gulp-js)