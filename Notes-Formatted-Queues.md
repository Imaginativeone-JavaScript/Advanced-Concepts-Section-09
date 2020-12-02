Notes-Formatted-Queues.md
## Lesson Taught

Stack and Queue Refresher

## What I Learned

```javascript
// Callback Queue (aka Task Queue)
function exploreJSRuntimeEnvironment() { 
  setTimeout(() => { console.log('1', 'This function spends some time outside of JavaScript (In the Browser\'s Web API). When it completes, it is sent to the call stack.') },  0) // Sent over to the Web API
  setTimeout(() => { console.log('2', 'This function also spends some time outside of JavaScript (In the Browser\'s Web API). When it completes, it\'s sent to the call stack.') }, 10) // Sent over to the Web API

  // When the web api work is done, responses are sent to the Callback Queue

  // 2 Job Queue
  // Promises are not part of the Web API, they're part of JavaScript
  // Another queue was created to offload Promise functionality, the "Job Queue" (also called the Microtask Queue).
  // From the Job Queue, it's sent to the Call Stack
  Promise.resolve('Job Queue Contents, after the Promise resolves, it is sent to the Call Stack').then((data) => console.log('2', data))

  // 3
  console.log('3', 'First Code to Execute, this function was sent directly to the Call Stack.') // This line is read into the call stack first, and then executed
}
```

## Thoughts and Questions

- The Web API work that's done in the Browser, is multithreaded? If it isn't multithreaded on the user's computer, does that cause the blocking that I'm trying to avoid?