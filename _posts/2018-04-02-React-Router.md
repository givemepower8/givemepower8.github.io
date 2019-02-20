---
layout: post
title: React Router
subtitle: React Router
date: 2018-04-02 08:39:22 -0800
categories: [React]
tags: [React, MERN]
---

# React Router

React is for developing a single page application. `<App />` is the root component.

Often the case, there are multiple bounded domains / context in the app, other libraries or frameworks like express.js, angular setup the routes for the app. [React Router](https://github.com/ReactTraining/react-router) is another light-weight implementation which is very flexible.

## Installation

`npm install -D react-router-dom`

## Basics

React router providers declarative routing for React.

```js
import { BrowserRouter } from 'react-router-dom';

ReactDOM.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>,
  el
);

const App = () => (
  <div>
    <nav>
      <Link to="/dashboard">Dashboard</Link>
    </nav>
    <div>
      <Route path="/dashboard" component={Dashboard} />
      <Route path="/withchildren" component={WithChildren} />
    </div>
  </div>
);

const WithChildren = ({ match }) => (
  <div>
    <Route path={match.url + '/firstChild'} component={FirstChild} />
    <Route path={match.url + '/secondChild'} component={SecondChild} />
  </div>
);
```

There are three types of components in React Router:

- router components, `<BrowserRouter>`, `<HashRouter>`, `<MemoryRouter>`, `<StaticRouter>`
- route matching components, `<Switch>`, `<Route>`
- and navigation components, `<Link>`, `<NavLink>`, `<Redirect>`, `<Prompt>`

All of the components that you use in a web application should be imported from react-router-dom.

react-router-dom provides `<BrowserRouter>` and `<HashRouter>` routers. `<BrowserRouter>` is usually used for a server that responds to requests.

There are two route matching components: `<Route>` and `<Switch>`.

`import { BrowserRouter, Route, Link } from 'react-router-dom`

A `<Switch>` will iterate over all of its children `<Route>` elements and only render the first one that matches the current location. It's useful when you need to render a "404" component).

```html
<Switch>
  <Route exact path='/' component={Home}/>
  <Route path='/about' component={About}/>
  <Route path='/contact' component={Contact}/>
  {/* when none of the above match, <NoMatch> will be rendered */}
  <Route component={NoMatch}/>
</Switch>
```

React Router provides a `<Link>` component to create links in your application. Wherever you render a `<Link>`, an anchor (`<a>`) will be rendered in your application's HTML.

## Parameters

Dynamic routing means routing takes place when the app is rendering.

## history

## Resources

[React Router docs](https://reacttraining.com/react-router/web/guides/philosophy)
