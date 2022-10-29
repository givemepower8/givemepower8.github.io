---
layout: post
title: React Components Lifecycle
subtitle: React Components Lifecycle
date: 2018-04-03 16:21:11 -0800
categories: [React]
tags: [React, MERN]
---

# Component lifecycle

The componentDidMount() method runs after the component output has been rendered to the DOM.

We will tear down the instances in the componentWillUnmount() lifecycle method.

[react-lifecycle-methods-diagram](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

The React component which extends React.Component goes through the following phases:

- Mounting
- Updating
- Unmounting

![The phases and methods of React lifecycle](https://cdn-images-1.medium.com/max/2000/1*lINPzI9FsJnay2_fm4vmzA.png){: width="800" }

or you can check the [lifecycle diagram here](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/).

More readings:

- [react component](https://reactjs.org/docs/react-component.html)
- [Understanding React — React 16.3 + Component life-cycle](https://medium.com/@baphemot/understanding-react-react-16-3-component-life-cycle-23129bc7a705)
- [React 16 Lifecycle Methods: How and When to Use Them](https://blog.bitsrc.io/react-16-lifecycle-methods-how-and-when-to-use-them-f4ad31fb2282)
- [understanding react v16.4 new component lifecycle methods](https://blog.bitsrc.io/understanding-react-v16-4-new-component-lifecycle-methods-fa7b224efd7d)
- [Update on Async Rendering](https://reactjs.org/blog/2018/03/27/update-on-async-rendering.html)
