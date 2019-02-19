---
layout: post
title: React Dev Environment
subtitle: React Dev Environment
date: 2018-05-01 16:21:11 -0800
categories: [React]
tags: [MERN, React]
---

# React Dev Environment

To me, Visual Studio Code is the great code editor for developing react applications.

## create-react-app

[create-react-app](https://github.com/facebook/create-react-app) is a global command-line utility to create new projects. It's boilerplate to create the continuous development environment.

[Getting Started](https://facebook.github.io/create-react-app/docs/getting-started)

## VS Code Support

### Add ESLint and Prettier to VS Code

`npm i -D eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react`

`npm i -D prettier eslint-config-prettier eslint-plugin-prettier`

`npm i -D husky lint-staged pretty-quick`

add the .eslintrc and .prettierrc file

in package.json

```js
  "precommit": "NODE_ENV=production lint-staged",
  "lint-staged": {
    "*.{js,jsx}": [
      "pretty-quick --staged",
      "eslint src/ --fix",
      "git add"
    ]
  },
```

### Unit test in VS Code

jest is used in create-react-app.

`npm i @types/jest` and enable jest in .eslintrc

```js
"env": {
    "jest": true
}
```

### Debugging in VS Code

Visual studio code supports to debug react app. Debugger for Chrome extension should be installed first.

Set the break points in the code, add the launch.json or it can be automatically generated in .vscode folder. Make sure the port is 3000 and `npm start` is run. The break points will be hit then.

```js
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",
            "url": "http://localhost:3000",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```

### Build and deploy

Run `npm run build` which will prepare the deploy package in build folder.

Use [serve](https://www.npmjs.com/package/serve) as a static web server to start from the build folder.

`npm install -g serve`

`serve -s build`

Now you can view the application locally.

To deploy, copy over the files in the build folder to the web server folder.

### Common Issues in VS Code

When you use auto format while saving in VS Code, for jsx files, the formatting sometimes will get wrong. Add the following in setting.json

```js
"beautify.ignore": [
        "**/*.js",
        "**/*.jsx"
    ]
```

Sometimes you will see the following error:

> There might be a problem with the project dependency tree.
> It is likely not a bug in Create React App, but something you need to fix locally.
>
> The react-scripts package provided by Create React App requires a dependency:
>
> ...

You can create a .env file and add 'SKIP_PREFLIGHT_CHECK=true'

## StoryBook

[StoryBook](https://storybook.js.org/basics/introduction/)

## React Developer Tools

[react developer tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)

## Visual Studio Code Support

[reactjs-tutorial](https://code.visualstudio.com/docs/nodejs/reactjs-tutorial)
