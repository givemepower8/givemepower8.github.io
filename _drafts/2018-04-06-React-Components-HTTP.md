---
layout: post
title: React Components HTTP
subtitle: React Components HTTP
date: 2018-04-06 16:21:11 -0800
categories: [React]
tags: [React, MERN]
---

# React Components HTTP

The componentDidMount() method runs after the component output has been rendered to the DOM. Ah this time, setState({...}) can update the component when the data is retrieved from AJAX calls. In short, populating data with AJAX calls should be wrapped in the componentDidMount lifecycle method.

You can use any AJAX library you like with React. Some popular ones are Axios, jQuery AJAX, and the browser built-in window.fetch.

For internet explorer, a promise polyfill is required.

```html
<script
  src="https://cdn.jsdelivr.net/npm/promise-polyfill@8/dist/polyfill.min.js"
  crossorigin
></script>
```

## whatwg-fetch

`npm install -D whatwg-fetch` or

```html
<script
  src="https://cdn.jsdelivr.net/npm/whatwg-fetch@3.0.0/dist/fetch.umd.min.js"
  crossorigin
></script>
```

For a items.json like following:

```json
{
  "items": [
    { "id": 1, "name": "Apples", "price": "$2" },
    { "id": 2, "name": "Peaches", "price": "$5" }
  ]
}
```

```js
class FetchExampleComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      error: null,
      isLoaded: false,
      items: []
    };
  }

  componentDidMount() {
    fetch('./items.json')
      .then(res => res.json())
      .then(
        result => {
          this.setState({
            isLoaded: true,
            items: result.items
          });
        },
        // Note: it's important to handle errors here
        // instead of a catch() block so that we don't swallow
        // exceptions from actual bugs in components.
        error => {
          this.setState({
            isLoaded: true,
            error
          });
        }
      );
  }

  render() {
    const { error, isLoaded, items } = this.state;
    if (error) {
      return <div>Error: {error.message}</div>;
    } else if (!isLoaded) {
      return <div>Loading...</div>;
    } else {
      return (
        <ul>
          {items.map(item => (
            <li key={item.name}>
              {item.name} {item.price}
            </li>
          ))}
        </ul>
      );
    }
  }
}
```

## axios

[axios](https://github.com/axios/axios) is Promise based HTTP client for the browser and node.js.

`npm install -D axios` or

```html
<script src="https://unpkg.com/axios/dist/axios.min.js" crossorigin></script>
```

```js
class AxiosExampleComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      error: null,
      isLoaded: false,
      items: []
    };
  }

  componentDidMount() {
    axios
      .get('./items.json')
      .then(response => {
        this.setState({
          isLoaded: true,
          items: response.data.items
        });
      })
      .catch(error => {
        this.setState({
          isLoaded: true,
          error
        });
      });
  }

  render() {
    const { error, isLoaded, items } = this.state;
    if (error) {
      return <div>Error: {error.message}</div>;
    } else if (!isLoaded) {
      return <div>Loading...</div>;
    } else {
      return (
        <ul>
          {items.map(item => (
            <li key={item.name}>
              {item.name} {item.price}
            </li>
          ))}
        </ul>
      );
    }
  }
}
```

More readings:

- [React AJAX FAQ](https://reactjs.org/docs/faq-ajax.html)
- [How to get "create-react-app" to work with your API](https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/)
- [weather-app](https://github.com/robwelan/weather-app)
