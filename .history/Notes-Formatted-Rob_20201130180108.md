# Asynchronous JavaScript

## Lesson Taught

- [x] 133225 09-01-10 0451 Section Overview Resources
Stack and Queue Refresher

## What I Learned

```javascript
function exploreJSRuntimeEnvironment() { 
  setTimeout(() => { console.log('1', 'This function spends some time outside of JavaScript (In the Browser\'s Web API)') },  0) // Sent over to the web api
  setTimeout(() => { console.log('2', 'This function also spends some time outside of JavaScript (In the Browser\'s Web API)') }, 10) // Sent over to the web api

  // When the web api work is done, responses are sent to the Callback Queue

  // 2
  // Job Queue
  Promise.resolve('hi').then((data) => console.log('2', data)) // Coming back to this

  // 3
  console.log('3', 'is a crowd') // This line is read into the call stack first, and then executed
}
```

## Thoughts and Questions

If I place exploreJSRuntimeEnvironment() into the JavaScript console without running it, "undefined" is printed. Why is that?

## Lesson Taught
Promises

## What I Learned

```javascript
// The very long way to do this
genericPromiseLong = new Promise((resolve) => { return resolve({ property: 'genericPromiseLong value' }) });
console.log('genericPromiseLong', genericPromiseLong);
```
### Some promises for testing purposes

```javascript
// A much shorter way to do this (Using Static Methods of the Promise Native JavaScript Object)
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve
const objPromise = Promise.resolve({ property: 'objPromise value' });
console.log(objPromise);

const arrPromise = Promise.resolve([ 'arrPromise value' ]);
console.log(arrPromise);

const funcPromise = Promise.resolve(namedFunction = function() { return 'named function returned this' });
console.log(funcPromise);
funcPromise.then(namedFunction);

const rejectedPromise = Promise.reject('This is the reason');
console.log(rejectedPromise);
```

### settlingPromises(iterable)

```javascript
const settlingPromises = Promise.allSettled([objPromise, arrPromise, funcPromise /*, rejectedPromise */]);
console.log(settlingPromises);
```

### Promise.any(iterable)

```javascript
const anyPromises = Promise.any([arrPromise, objPromise, funcPromise /*, rejectedPromise */]);
console.log(anyPromises);
```

### Degenerate Situations
```javascript
// Degenerate Situations
// In this case, 'promise' remains pending forever, and its result is undefined
const promise = new Promise((resolve, reject) => {});
console.log('promise', promise);

// Even though there's not a (planned) 'rejected' state, this promise is rejected
// and breaks the app
const promise = new Promise((resolve) => { throw Error; });
console.log('promise', promise);
```

## Thoughts and Questions

- Promise.allSettled() appears to remain pending. Should it do that?







## Lesson Taught
Template

## What I Learned
Template

## Thoughts and Questions
Template
