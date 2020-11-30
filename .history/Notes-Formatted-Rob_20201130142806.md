# Asynchronous JavaScript

## Lesson Taught

- [x] 133225 09-01-10 0451 Section Overview Resources
Stack and Queue Refresher

## What I Learned

```javascript
function exploreJSRuntimeEnvironment() {
  setTimeout(() => { console.log('1', 'This function spends some time outside of JavaScript (Web API)') },  0) // Sent over to the web api
  setTimeout(() => { console.log('2', 'This function also spends some time outside of JavaScript') }, 10) // Sent over to the web api

  // When the web api work is done, responses are sent to the Callback Queue

  // 2
  // Job Queue
  Promise.resolve('hi').then((data) => console.log('2', data)) // Coming back to this

  // 3
  console.log('3', 'is a crowd') // This line is read into the call stack first, and then executed
}
```

## Thoughts and Questions
Template








## Lesson Taught
Template

## What I Learned
Template

## Thoughts and Questions
Template
