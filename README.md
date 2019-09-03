# compose-app

[![Greenkeeper badge](https://badges.greenkeeper.io/JustinDFuller/compose-app.svg)](https://greenkeeper.io/)

Example of creating an entire app through function composition

## What?

This app uses composition/reducers to create an almost linear flow. Each step can (but doesn't have to) return an object. That object will be frozen and merged with all objects that came before it. This allows you to incrementally piece together your app.

Each step is a function, and uses the results of all the previous functions as it's main argument. Since each piece of your app is a function this makes it extremely simple to test. You simply pass in what you expect it to use. No need for proxyquire!

## How?

The flow is something like this.

1. Get configuration (env variables).
2. Get dependencies.
3. Create logger.
4. Connect to database and initialize models.
5. Create sockets.
6. Create routes.
7. Initialize the app.


Each step has the results of the last that can be used (but not modified).

## Async

The main reducer supports promises. For example the database step authenticates and syncs before it moves on. These are both async functions.
