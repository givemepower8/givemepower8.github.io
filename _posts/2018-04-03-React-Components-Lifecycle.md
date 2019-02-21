---
layout: post
title: React Components Lifecycle
subtitle: React Components Lifecycle
date: 2018-04-01 16:21:11 -0800
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

More readings:

- [understanding react v16.4 new component lifecycle methods](https://blog.bitsrc.io/understanding-react-v16-4-new-component-lifecycle-methods-fa7b224efd7d)
