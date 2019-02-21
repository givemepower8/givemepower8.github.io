---
layout: post
title: React Components JSX
subtitle: React Components
date: 2018-04-02 16:21:11 -0800
categories: [React]
tags: [React, MERN]
---

# JSX

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

## Conditional rendering

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

## Preventing Component from Rendering

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

## Rendering Multiple Components

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
