---
layout: post
title: React Components
subtitle: React Components
date: 2018-04-01 16:21:11 -0800
categories: [React]
tags: [React, MERN]
---

# React Component

[what framework to choose in 2018](https://medium.com/@TechMagic/reactjs-vs-angular5-vs-vue-js-what-to-choose-in-2018-b91e028fa91d)

> React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.
>
> Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called "components" that contain both.

Some benefits of components:

- Declarative programming
  - Declarative views make code more predictable and easier to debug.
  - Design simple views for each state in your application, and React will efficiently update and render just the right components when your data changes.
- Components over DOMs
  - Focus on Apps, no html predefined, DOM elements are dynamically injected
  - Components should be simple
- Build encapsulated components that manage their own state, then compose them to make complex UIs.
  - component focuses on making thing works, not limited by existing html structure
- Development can be incremental
  - Components are testable
- Performance should be great
- A JavaScript error in a part of the UI shouldn’t break the whole app.

## How to write components

[react-component](https://reactjs.org/docs/react-component.html)

Components are UIs with programmable props and states.

Virtually, components are like div elements or other container elements. Usually all the components are in one app component, like the DOM tree structure, components can have parent, ancestors, children, descendants, siblings, etc,. App component is the root.

Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called "props") and return React elements describing what should appear on the screen.

```js
var Hello = function(props) {
  render() {
    return <div>Hello {props.toWho}</div>;
  }
}

ReactDOM.render(
  <Hello toWho="World" />,
  document.getElementById('root')
);
```

The above is known as function components which can be written in ECMAScript 6 class component which inherited from React.Component as following.

```js
class Hello extends React.Component {
  render() {
    return <div>Hello {this.props.toWho}</div>;
  }
}

ReactDOM.render(<Hello toWho="World" />, document.getElementById('root'));
```

Function components are the best components when it comes to reusability because they are pure function with no state. They are predictable—the same input will always give us the same output.

React.Component has its life cycle and has constructor, properties and methods:

- Class Properties
  - defaultProps
  - displayName
- Instance Properties
  - props
  - state
- Methods
  - setState()
  - forceUpdate()

### JSX

[introducing-jsx](https://reactjs.org/docs/introducing-jsx.html)

[jsx-in-depth](https://reactjs.org/docs/jsx-in-depth.html)

[react-without-jsx](https://reactjs.org/docs/react-without-jsx.html)

```js
class HelloMessage extends React.Component {
  render() {
    return <div>Hello {this.props.name}</div>;
  }
}

ReactDOM.render(<HelloMessage name="Taylor" />, mountNode);
```

The above is transpiled to the following:

```js
class HelloMessage extends React.Component {
  render() {
    return React.createElement('div', null, 'Hello ', this.props.name);
  }
}

ReactDOM.render(
  React.createElement(HelloMessage, { name: 'Taylor' }),
  mountNode
);
```

Like XAML in the .net world, jsx enables html tags can be written directly in the code.

### ReactDOM.render

In addition to taking input data (accessed via this.props), a component can maintain internal state data (accessed via this.state).

When a component's state data changes, the rendered html markup will be updated by re-invoking render().

In practice, most React apps only call ReactDOM.render() once.

### props

props are parameter which takes in the arguments from JSX.

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(element, document.getElementById('root'));
```

[render-props](https://reactjs.org/docs/render-props.html)

### state

[state-and-lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)

[lifting-state-up](https://reactjs.org/docs/lifting-state-up.html)

setState({…})

### constructor

### Collection

#### map

#### key

### Validation

#### PropTypes

### pass data between components

#### Context

[Context](https://reactjs.org/docs/context.html)

Context is designed to share data that can be considered “global” for a tree of React components, such as the current authenticated user, theme, or preferred language.

Context id shared by different components, usually we pass props in the component hierarchy, but for some concept like theme, sign-in, toaster, etc., those ones can be accessed by any component by context.

#### parent -> child

#### child -> parent

### Component lifecycle

### Lifecycle

[react-lifecycle-methods-diagram](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

Mounting

Updating

Unmounting

### Error Handling

[Error Handling](https://reactjs.org/docs/error-boundaries.html)

## Form

[formik](https://jaredpalmer.com/formik)

## Events

## Timers

```js
class Timer extends React.Component {
  constructor(props) {
    super(props);
    this.state = { seconds: 0 };
  }

  tick() {
    this.setState(state => ({
      seconds: state.seconds + 1
    }));
  }

  componentDidMount() {
    this.interval = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.interval);
  }

  render() {
    return <div>Seconds: {this.state.seconds}</div>;
  }
}

ReactDOM.render(<Timer />, mountNode);
```

## AJAX

[React AJAX FAQ](https://reactjs.org/docs/faq-ajax.html)

[How to get "create-react-app" to work with your API](https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/)

[weather-app](https://github.com/robwelan/weather-app)

## Resources

[nextjs](https://nextjs.org/learn)

### Examples

[vscode-react-sample](https://github.com/Microsoft/vscode-react-sample)
