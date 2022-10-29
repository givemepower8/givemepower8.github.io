---
layout: post
title: React Components Events
subtitle: React Components Events
date: 2018-04-04 16:21:11 -0800
categories: [React]
tags: [React, MERN]
---

# Events

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

## Passing Arguments to Event Handlers

Inside a loop it is common to want to pass an extra parameter to an event handler.

For example, if id is the row ID and you have the deleteRow(id, event) function, either of the following would work:

```js
<button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>
<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
```

More readings:

- [SyntheticEvent](https://reactjs.org/docs/events.html)
