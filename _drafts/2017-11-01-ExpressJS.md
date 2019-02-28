# Express

```js
const express = require('express');

const app = express();
app.use(express.static('static'));
```

```js
// or you can specify the folder
app.use('/public', express.static('static'));
```

The above would have mounted the static files on the path /public and all static files would have to be accessed with the prefix /public, for example, /public/index.html.

## Routes

```js
app.get('/hello', (req, res) => {
  res.send('hello world');
});
```

### Route parameters

`app.get('/customers/:customerId', (req, res) => {...});`

The URL /customers/1234 will match the above route specification, and so will /customers/4567. In either case, the customer ID will be captured and supplied to the
handler function as part of the request in req.params, with the name of the parameter as the key. Thus, req.params.customerId will have the value 1234 or 4567 for each of these URLs, respectively.

You can have multiple parameters, for example `/customers/:customerId/orders/:orderId`, to match a customer's order.

Router does not try to find a best match; instead, it tries to match all routes in the order and the first match is used. A pattern like `/api/*`, you should add this route only after all the specific routes.

### Request

[Request](http://expressjs.com/en/api.html#req)

[Node.js request object](https://nodejs.org/api/http.html#http_class_http_incomingmessage)

You can access a parameter value using req.params.

req.query: This holds a parsed query string. It's an object with keys as the query string parameters and values as the query string values. Multiple keys with the same name are converted to arrays, and keys with a square bracket notation result in nested objects (e.g., order[status]=closed can be accessed as req.query.
order.status).

req.header, req.get(header): The get method gives access to any header in the request. The header property is an object with all headers stored as key-value pairs. Some headers are treated specially (like Accept), and have dedicated methods in the request object for them. That’s because common tasks that depend on these headers can be easily handled.

req.path: This contains the path part of the URL, that is, everything up to any ? that starts the query string. Usually, the path is part of the route if the route is not a pattern, but if the path is a pattern that can match different URLs, you can use this property to get the actual path that was received in the request.

req.url, req.originalURL: These properties contain the complete URL, including the query string. Note that if you have any middleware that modifies the request URL, originalURL will hold the URL as it was received, before the modification.

req.body: This contains the body of the request, valid for POST, PUT, and PATCH requests. Note that the body is not available (req.body will be undefined) unless a middleware is installed to read and optionally interpret or parse the body.

#### request body

Express does not have an in-built parser that can parse request bodies to convert them into objects.

The package body-parser can parse various types of request bodies including URL Encoded form data and JSON.

`npm install body-parser --save`

```js
const bodyParser = require('body-parser');
app.use(bodyParser.json());

//...
```

### Response

[Response](http://expressjs.com/en/api.html#res)

[Node.js Response object](https://nodejs.org/api/http.html#http_class_http_serverresponse)

The response object is used to construct and send a response to a request.

res.send(body): You already saw the res.send() method briefly, which responded with a string. This method can also accept a buffer (in which case the content type is set as application/octet-stream as opposed to text/html in case of a string). If the body is an object or an array, it is automatically converted to a
JSON string with an appropriate content type.

res.status(code): This sets the response status code. If not set, it is defaulted to 200 OK. One common way of sending an error is by combining the status() and send() methods in a single call like res.status(403).send("Access Denied").

res.json(object): This is the same as res.send(), except that this method forces conversion of the parameter passed into a JSON, whereas res.send() may treat some parameters like null differently. It also makes the code readable and explicit, stating that you are indeed sending out a JSON.

res.sendFile(path): This responds with the contents of the file at path. The content type of the response is guessed using the extension of the file.

```js
res.json({ _metadata: metadata, records: issues });
```

The above is actually a shortcut for the following:

```js
res.set('Content-Type', 'application/json');
res.send(JSON.stringify({ _metadata: metadata, records: issues }));
```

## Middleware

Express is a web framework that has minimal functionality of its own. An Express application is essentially a series of middleware function calls. In fact, the Router itself is nothing but a middleware function.

`app.use(...)`

### multer

[multer](https://www.npmjs.com/package/multer)

## Resources

[express](https://devdocs.io/express/)

[expressjs tutorial](https://www.tutorialspoint.com/expressjs/index.htm)

[Logging in a Node.js Express app with Morgan and Bunyan](https://medium.com/@tobydigz/logging-in-a-node-express-app-with-morgan-and-bunyan-30d9bf2c07a)
