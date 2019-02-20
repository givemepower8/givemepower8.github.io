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
  - We have limited HTML tags. Declarative components extends HTML tag make code more readable.
  - Design simple UIs for each state in your application, and React will efficiently update and render just the right components when your data changes.
- More maintainable code
  - Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.
  - Focus on Apps and making thing works, no DOM structures, dynamically injected DOM elements tricks
  - Components can be stateless or stateful
  - Components are reuseable, always split components into smaller components
- Development can be incremental
  - stateless components are predictable and easier to debug
  - Components are testable
  - JavaScript error in component shouldn't break the whole app.
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

Components can refer to other components in their output. In the following example, People contains a list of Person components.

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

props are parameter which takes in the arguments from JSX. The props are mapped to the attributes inside the component tags.

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

## JSX

JSX looks like a template language you directly write in JavaScript, usually in the return block in functional components, and in the render method in class-based component.

More than a a template language, JSX comes with the full power of JavaScript. Under the hood, JSX is transpiled into JavaScript to produce React elements.

Inside JSX, we wrap variables in curly braces. You can put any valid JavaScript expression or call a JavaScript function inside the curly braces.

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

You can use curly braces to embed a JavaScript expression in an attribute:

```js
const element = <img src={user.avatarUrl} />;
```

Don't put quotes around curly braces when embedding a JavaScript expression in an attribute. You should either use quotes (for string values) or curly braces (for expressions), but not both in the same attribute. React DOM uses camelCase property naming convention instead of HTML attribute names. For example, class becomes className in JSX, and tabindex becomes tabIndex.

JSX tags may contain children:

```js
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

By default, React DOM escapes any values embedded in JSX before rendering them. Thus it ensures that you can never inject anything that's not explicitly written in your application. Everything is converted to a string before being rendered. This helps prevent XSS (cross-site-scripting) attacks.

### Conditional rendering

You can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions:

```js
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}

const element = <h1>Hello, {formatName(user)}!</h1>;

ReactDOM.render(element, document.getElementById('root'));
```

To avoid create spaghetti JSX code, always remember that whenever conditions become too complex, it might be a good time to extract a component or use some functions.

You may embed any expressions in JSX by wrapping them in curly braces. This includes the JavaScript logical && operator. It can be handy for conditionally including an element:

```js
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 && (
        <h2>You have {unreadMessages.length} unread messages.</h2>
      )}
    </div>
  );
}

const messages = ['React', 'Re: React', 'Re:Re: React'];
ReactDOM.render(
  <Mailbox unreadMessages={messages} />,
  document.getElementById('root')
);
```

It works because in JavaScript, true && expression always evaluates to expression, and false && expression always evaluates to false. If the condition is true, the element right after && will appear in the output. If it is false, React will ignore and skip it.

Another method for conditionally rendering elements inline is to use the JavaScript conditional operator condition ? true : false.

```js
render() {
  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
      The user is <b>{isLoggedIn ? 'currently' : 'not'}</b> logged in.
    </div>
  );
}

// or something like:
render() {
  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
      {isLoggedIn ? (
        <LogoutButton onClick={this.handleLogoutClick} />
      ) : (
        <LoginButton onClick={this.handleLoginClick} />
      )}
    </div>
  );
}
```

### Preventing Component from Rendering

In rare cases you might want a component to hide itself even though it was rendered by another component. To do this return null instead of its render output.

```js
function WarningBanner(props) {
  if (!props.warn) {
    return null;
  }

  return <div className="warning">Warning!</div>;
}

class Page extends React.Component {
  constructor(props) {
    super(props);
    this.state = { showWarning: true };
    this.handleToggleClick = this.handleToggleClick.bind(this);
  }

  handleToggleClick() {
    this.setState(state => ({
      showWarning: !state.showWarning
    }));
  }

  render() {
    return (
      <div>
        <WarningBanner warn={this.state.showWarning} />
        <button onClick={this.handleToggleClick}>
          {this.state.showWarning ? 'Hide' : 'Show'}
        </button>
      </div>
    );
  }
}

ReactDOM.render(<Page />, document.getElementById('root'));
```

### Rendering Multiple Components

```js
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map(number => <li>{number}</li>);
const list = <ul>{listItems}</ul>;
```

Run the above, you will see a warning that a key should be provided for list items. A key is a special string attribute you need to include when creating lists of elements.

Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity:

```js
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map(number => (
  <li key={number.toString()}>{number}</li>
));
const list = <ul>{listItems}</ul>;
```

The best way to pick a key is to use a string that uniquely identifies a list item among its siblings.

```js
const todoItems = todos.map(todo => <li key={todo.id}>{todo.text}</li>);
```

When you don't have stable IDs for rendered items, you may use the item index as a key as a last resort:

```js
const todoItems = todos.map((todo, index) => (
  // Only do this if items have no stable IDs
  <li key={index}>{todo.text}</li>
));
```

It's not recommend using indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state.

Keys only make sense in the context of the surrounding array.

For example, if you extract a ListItem component, you should keep the key on the `<ListItem />` elements in the array rather than on the `<li>` element in the ListItem itself.

```js
function ListItem(props) {
  // Correct! There is no need to specify the key here:
  return <li>{props.value}</li>;
}

function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map(number => (
    // Correct! Key should be specified inside the array.
    <ListItem key={number.toString()} value={number} />
  ));
  return <ul>{listItems}</ul>;
}

const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList numbers={numbers} />,
  document.getElementById('root')
);
```

Useful readings:

- [introducing-jsx](https://reactjs.org/docs/introducing-jsx.html)
- [jsx-in-depth](https://reactjs.org/docs/jsx-in-depth.html)
- [react-without-jsx](https://reactjs.org/docs/react-without-jsx.html)

## Component lifecycle

The componentDidMount() method runs after the component output has been rendered to the DOM.

We will tear down the instances in the componentWillUnmount() lifecycle method.

[react-lifecycle-methods-diagram](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

Mounting

Updating

Unmounting

## Events

React events look similar to DOM events. They are named using camelCase, rather than lowercase.

A simple example:

```js
function ActionLink() {
  function handleClick(e) {
    e.preventDefault();
    console.log('The link was clicked.');
  }

  return (
    <a href="#" onClick={handleClick}>
      Click me
    </a>
  );
}
```

You cannot return false to prevent default behavior in React. You must call preventDefault explicitly.

With JSX you pass a function as the event handler, rather than a string.

When you define a class-based component, a common pattern is for an event handler to be a method on the class.

Please notice the binding syntax in the constructor.

```js
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = { isToggleOn: true };

    // This binding is necessary to make `this` work in the callback
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(state => ({
      isToggleOn: !state.isToggleOn
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}

ReactDOM.render(<Toggle />, document.getElementById('root'));
```

In the above code, if you forget to bind this.handleClick and pass it to onClick, "this" will be undefined when the function is actually called.

If you don't like this syntax, there are two ways you can get around this.

```js
handleClick = () => {
  this.setState(state => ({
    isToggleOn: !state.isToggleOn
  }));
};
```

This above syntax is the experimental public class fields syntax which is enabled by default in Create React App.

If you aren't using the above two, you can use an arrow function in the callback of button onClick:

```js
// This syntax ensures `this` is bound within handleClick
return <button onClick={e => this.handleClick(e)}>Click me</button>;
```

The problem with this syntax is that a different callback is created each time the Toggle renders. In most cases, this is fine. However, if this callback is passed as a prop to lower components, those components might do an extra re-rendering. It is recommend binding in the constructor or using the class fields syntax, to avoid this sort of performance problem.

Another example:

```js
class LoginControl extends React.Component {
  constructor(props) {
    super(props);
    this.handleLoginClick = this.handleLoginClick.bind(this);
    this.handleLogoutClick = this.handleLogoutClick.bind(this);
    this.state = { isLoggedIn: false };
  }

  handleLoginClick() {
    this.setState({ isLoggedIn: true });
  }

  handleLogoutClick() {
    this.setState({ isLoggedIn: false });
  }

  render() {
    const isLoggedIn = this.state.isLoggedIn;
    let button;

    if (isLoggedIn) {
      button = <LogoutButton onClick={this.handleLogoutClick} />;
    } else {
      button = <LoginButton onClick={this.handleLoginClick} />;
    }

    return (
      <div>
        <Greeting isLoggedIn={isLoggedIn} />
        {button}
      </div>
    );
  }
}

ReactDOM.render(<LoginControl />, document.getElementById('root'));
```

### Passing Arguments to Event Handlers

Inside a loop it is common to want to pass an extra parameter to an event handler.

For example, if id is the row ID and you have the deleteRow(id, event) function, either of the following would work:

```js
<button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>
<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
```

More readings:

- [SyntheticEvent](https://reactjs.org/docs/events.html)

## Validation

### PropTypes

## Pass data between components

### Context

[Context](https://reactjs.org/docs/context.html)

Context is designed to share data that can be considered "global" for a tree of React components, such as the current authenticated user, theme, or preferred language.

Context id shared by different components, usually we pass props in the component hierarchy, but for some concept like theme, sign-in, toaster, etc., those ones can be accessed by any component by context.

### parent -> child

### child -> parent

## Error Handling

[Error Handling](https://reactjs.org/docs/error-boundaries.html)

## Styling

className

## Form

### text box input

```js
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = { value: '' };

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({ value: event.target.value });
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input
            type="text"
            value={this.state.value}
            onChange={this.handleChange}
          />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

### select option

### Formik

If you’re looking for a complete solution including validation, keeping track of the visited fields, and handling form submission, [Formik](https://jaredpalmer.com/formik) is one of the popular choices.

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

- burger builder
  - [ReactJS-burger-builder](https://codesandbox.io/s/github/Deepak2607/ReactJS-burger-builder/tree/master/)
  - [burger-builder-react](https://github.com/kinny94/burger-builder-react)
