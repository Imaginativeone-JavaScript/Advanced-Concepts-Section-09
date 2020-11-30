# Asynchronous JavaScript

## Lesson Taught
Template

## What I Learned
Template

## Thoughts and Questions
Template

```javascript
setTimeout(() => { console.log('1', 'is the loneliest number') },  0) // Sent over to the web api
setTimeout(() => { console.log('2', 'can be as bad as one')    }, 10) // Sent over to the web api

// When the web api calls are done, their responses are sent to the Callback Queue

// 2
// Job Queue
Promise.resolve('hi').then((data) => console.log('2', data)) // Coming back to this

// 3
console.log('3', 'is a crowd') // This line is read into the call stack first, and then executed
```
