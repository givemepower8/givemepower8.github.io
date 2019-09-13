# webpack-dev-server

[webpack-dev-server](https://github.com/webpack/webpack-dev-server)

`npm install webpack-dev-server --save-dev`

To start the server:

`node_modules\.bin\webpack-dev-server` or `npx webpack-dev-server`

Or add `"start": "webpack-dev-server --open",` in package.json

```js
{
    "scripts": {
        "start": "webpack-dev-server --open",
        "build": "webpack --config webpack.config.js",
        "test": "echo \"Error: no test specified\" && exit 1"
  }
}
```

in webpack.config.js file to specify the devServer contentBase

```js
module.exports = {
  devServer: {
    contentBase: './dist'
  }
};
```

now `npm start` will launch the webpack-dev-server.

`webpack-dev-server --hot --inline`

`"dev": "webpack-dev-server --inline --content-base ./public --open",`
