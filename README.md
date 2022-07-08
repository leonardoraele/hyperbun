# HyperBun is meant for Bun runtimes, it will not work in Node / Deno.

A simple HTTP routing library built on top of Bun's built in HTTP solution.

## Getting started

    bun add hyperbun

## Example

```ts
import {createServer} from 'hyperbun';

const server = createServer();

server.middleware((request, next) => {
  console.log('Just a simple middleware...');
});

server.middleware((request, next) => {
  return next(Error('Oops, I returned a 500.'));
});

server.get('/json', (request) => {
  return {
    hello: 'I will automatically become a JSON response...'
  }
});

server.get('/text', (request) => {
  return "Hello, I will be a text/html response...";
});

server.listen({
  port: 3000,
  hostname: '0.0.0.0'
});
```

## Not nearly ready yet..

You can probably use it for the most basic HTTP server, but there are maaaany things missing and in progress. So probably don't.

## Available methods

These listeners will automatically match the route and method that you setup and respond with a 404 for ones you don't have.

`server.get`
`server.post`
`server.put`
`server.delete`