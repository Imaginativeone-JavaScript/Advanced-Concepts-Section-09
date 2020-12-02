Notes-Formatted-Promises.md
# Asynchronous JavaScript
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
const settlingPromises = Promise.allSettled([objPromise, arrPromise, funcPromise, rejectedPromise]);
console.log(settlingPromises);
```

### Promise.any(iterable)

```javascript
const anyPromises = Promise.any([arrPromise, objPromise, funcPromise, rejectedPromise]);
console.log(anyPromises);
anyPromises.then((data) => {
  console.log(data);
})
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
- The point might be that I can use the resolved value.
  - After the value is used, the anyPromise variable is changed to "fulfilled" with a value of undefined
