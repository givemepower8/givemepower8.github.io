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
  - We compose html with HTML tags / elements. UI and Logic has tight dependency on how html elements are composed. React components enable declarative programming extends HTML tag to make code more readable.
  - Components has it's own events like onChange, onClick which makes the code easy to understand.
- More maintainable code
  - Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.
  - Focus on Apps and making thing works, no DOM structures, dynamically injected DOM elements tricks
  - React takes care to efficiently update and render just the right components when your data changes.
  - Components are reuseable, always split components into smaller components
- Development can be incremental
  - Stateless components are predictable and easier to debug
  - Stateful component has responsibility over a single part of the functionality provided by the component, and that responsibility is entirely encapsulated by the component.
  - components are testable
  - JavaScript error in component shouldn't break the whole web app.
- Performance should be great
  - Components are virtual DOM

## How to write components

Components are UIs with programmable props, states, events and more.

Virtually, components are like div elements or other container elements. Or you can think that an app component consists of header component, navigation component, sidebar component, content component, etc.,. Usually all the components are in one app component, like the DOM tree structure, each component can have one parent, ancestors, children, descendants, siblings, etc,. App component is the root.

Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called "props") and return React elements rendering on the screen.

```js
var Hello = function(props) {
  return <div>Hello {props.toWho}</div>;
};

// the above can be written as following:
// const Hello = (props) => { return <div>Hello {props.toWho}</div> };

ReactDOM.render(<Hello toWho="World" />, document.getElementById('root'));
```

The above is known as functional components which can be written in ECMAScript 6 class-based component which inherited from React.Component as following.

```js
class Hello extends React.Component {
  render() {
    return <div>Hello {this.props.toWho}</div>;
  }
}

ReactDOM.render(<Hello toWho="World" />, document.getElementById('root'));
```

Functional components are the best components when it comes to reusability because they are pure function with no state. They are very predictable as the same input will always give us the same output.

But sometimes you need state inside the component, class-based component or React.Component supports state and it has its life cycle and has constructor, properties and methods:

- Class Properties
  - defaultProps
  - displayName
- Instance Properties
  - props
  - state
- Methods
  - setState()
  - forceUpdate()

### Parent Children components

Parent components can refer to children components in their output. In the following example, People contains a list of Person components.

```js
function People(props) {
  return (
    <div>
      {props.people.map((person, index) => (
        <Person key={index} person={person} />
      ))}
    </div>
  );
}

function Person(props) {
  const person = props.person;
  return (
    <div className="person">
      <h1>{person.name}</h1>
      <p>Your Age: {person.age}</p>
    </div>
  );
}

const people = [{ name: 'Max', age: '28' }, { name: 'Tom', age: '29' }];

ReactDOM.render(<People people={people} />, document.getElementById('root'));
```

More readings:

- [react-component](https://reactjs.org/docs/react-component.html)

### props

Parent component communicates with children components using props. props are parameter which takes in the arguments from JSX. The props are mapped to the attributes inside the component tags.

[render-props](https://reactjs.org/docs/render-props.html)

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(element, document.getElementById('root'));
```

### state

State is similar to props, but it is private and fully controlled by the component. Usually props takes input data to initialize the component, a component can maintain internal state data, accessed via this.state.

Class components should always call the base constructor with props.

```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date() };
  }

  componentDidMount() {
    this.timerID = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.timerID);
  }

  tick() {
    this.setState({
      date: new Date()
    });
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

[state-and-lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)

[lifting-state-up](https://reactjs.org/docs/lifting-state-up.html)

#### setState()

When a component's state data changes, the rendered html markup will be updated. This is done by setState() call, React knows the state has changed, and calls the render() method.

Because this.props and this.state may be updated asynchronously, you should not rely on their values for calculating the next state.

```js
// Wrong
incrementCount() {
  // Note: this will *not* work as intended.
  this.setState({count: this.state.count + 1});
}

// Correct
incrementCount() {
  this.setState((state) => {
    // Important: read `state` instead of `this.state` when updating.
    return {count: state.count + 1}
  });
}

handleSomething() {
  // Let's say `this.state.count` starts at 0.
  this.incrementCount();
  this.incrementCount();
  this.incrementCount();
}
```

if you need to update both state and props

```js
// Wrong
this.setState({
  counter: this.state.counter + this.props.increment
});

// Correct
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```

Usually ajax calls are wrapped in componentDidMount. When you call setState(), React merges the object you provide into the current state.

```js
componentDidMount() {
  fetchPosts().then(response => {
    this.setState({
      posts: response.posts
    });
  });

  fetchComments().then(response => {
    this.setState({
      comments: response.comments
    });
  });
}
```

The merging is shallow, so this.setState({comments}) leaves this.state.posts intact, but completely replaces this.state.comments.

#### state guidelines

State is often local or encapsulated. It is not accessible to any component other than the one that owns and sets it. Neither parent nor child components can know if a certain component is stateful or stateless, if you are trying to walk around to set other component's state, there might be a design problem.

A component may choose to pass its state down as props to its child components. Any state is owned by some specific component, and any data or UI derived from that state can only affect components "below" them in the tree.

You can use stateless components inside stateful components, and vice versa.

### ReactDOM.render

JSX is to create the React elements. React elements are presented in React DOM or virtual DOM. ReactDOM.render renders the React elements to a real DOM node.

React elements are immutable. Once you create an element, you can't change its children or attributes. React element represents the UI at a certain point in time.

Once render is called, React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

React apps usually have a single root DOM node in the index.html.

```js
ReactDOM.render(element, document.getElementById('root'));
```

You can call render as many times as you want, but as a good practice, most React apps only call ReactDOM.render() once.

## Validation

### PropTypes

## Communication between components

Communication between components depends on the direction.

### Context

[Context](https://reactjs.org/docs/context.html)

Context is designed to share data that can be considered "global" for a tree of React components, such as the current authenticated user, theme, or preferred language.

Context id shared by different components, usually we pass props in the component hierarchy, but for some concept like theme, sign-in, toaster, etc., those ones can be accessed by any component by context.

### parent -> children

Parents communicates to children via props. When states change, props change.

[Simple Cart](https://codepen.io/hermantnet/pen/EgWEom?editors=1010)

### child -> parent

Children communicate to parents via callbacks.

### Redux

## Error Handling

[Error Handling](https://reactjs.org/docs/error-boundaries.html)

## Styling

className

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

## Resources

[React Fiber Architecture](https://github.com/acdlite/react-fiber-architecture)

[React Enlightenment](https://www.reactenlightenment.com/what-is-react.html)

[nextjs](https://nextjs.org/learn)

[React Community](https://github.com/reactjs)

### Examples

[React University](https://github.com/react-u/)
[vscode-react-sample](https://github.com/Microsoft/vscode-react-sample)

- burger builder

  - [ReactJS-burger-builder](https://codesandbox.io/s/github/Deepak2607/ReactJS-burger-builder/tree/master/)
  - [burger-builder-react](https://github.com/kinny94/burger-builder-react)

- shopping cart
  - [real time cart](https://deepstreamhub.com/tutorials/example-apps/realtime-cart/)
  - [shopping cart](https://github.com/sivadass/react-shopping-cart)
  - [react-shopping-cart](https://github.com/Gigacore/react-shopping-cart)
