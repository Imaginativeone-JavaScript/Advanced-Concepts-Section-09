- [ ] Section 9: Asynchronous JavaScript 00/11 | 1hr 56min
	- [ ] 133. Section Overview | 5min Resources
	  - Web APIs
		- Callbacks
		- What does "asynch" mean? "We don't have it right now. We need to get it."

		```javascript
		// Callback Queue
		setTimeout(() => { console.log('1', 'is the loneliest number') }, 0)
		setTimeout(() => { console.log('2', 'can be as bad as one') }, 2000)

		// 2
		// Job Queue
		Promise.resolve('hi').then((data) => console.log('2', data))

		// 3
		console.log('3', 'is a crowd')

		// 3 is a crowd
		// 2 hi
		// undefined
		// 1 is the loneliest number
		// 2 can be as bad as one
		```

	- [ ] 134. Quick Note: Upcoming Videos | 1min // Skip to 140
	- [ ] 135. How JavaScript Works | 24min
	- [ ] 136. Promises | 22min
	- [ ] 137. ES8 - Async Await | 15min
	- [ ] 138. ES9 (ES2018) | 5min
	- [ ] 139. ES9 (ES2018) - Async | 11min

	- [ ] 140. Job Queue | 7min Resources
	  - The addition of Promises in ES6 required changes in the Event Loop
		- Callback Queue/Task Queue
		- With Promises, we now have a Native (JavaScript) way to handle asynchronous code
		- Promises are not part of the Web API, they are part of JavaScript
		- Enter, the "Job Queue" aka "Microtask Queue"
		- The Job Queue is "smaller" than the Callback Queue AND has a higher priority
		  - The Event Loop checks the Job Queue first. When it's empty, it checks the callback queue.
		- Implemented by the Browser
	
	- [ ] 141. Promises: Parallel, Sequential and Race | 10min Resources

	```javascript
	const promisify = (item, delay) =>
		new Promise((resolve) =>
			setTimeout(() =>
				resolve(item), delay));

		const a = () => promisify('a', 100);
		const b = () => promisify('b', 5000);
		const c = () => promisify('c', 3000);

		// console.log(a(), b(), c()) // Three Promises

		async function parallel() {
			const promises = [a(), b(), c()];
			const [output1, output2, output3] = await Promise.all(promises);
			return `parallel is done: ${output1} ${output2} ${output3}`
	}

	// parallel().then(console.log); // parallel is done: a b c

	async function race() {
		const promises = [a(), b(), c()];
		const output1 = await Promise.race(promises);
		return `race is done: ${output1}`;
	}

	// race().then(console.log); // race is done: a

	async function sequence() {		// not using a special Promise function here
		const output1 = await a();
		const output2 = await b();
		const output3 = await c();
		return `sequence is done ${output1} ${output2} ${output3}`
	}

	sequence().then(console.log)
	parallel().then(console.log)
	race().then(console.log)

	// sequence().then(console.log); // sequence is done: a b c
	```

	- [ ] 142. ES2020: allSettled() | 4min // ?

	- [ ] 143. Threads, Concurrency and Parallelism | 11min Resources
	  - Javascript is a single-threaded language
		- With the asynchronous model, things still happen in the background
		  - Web Workers
			  - Passed off to "LIBUV"

	```javascript
	var worker = new Worker('worker.js'); // Used with Node
	worker.postMessage('Helloooo')

	addEventListener('message');

	// fetch() // facade function, uses the Web API

	// Node
	const { spawn } = require('child_process') // Node child process module

	spawn('get', ['stuff'])
	```
- [ ] Section 10: Modules In JavaScript 00/07 | 53min
	- [ ] 144. Section Overview | 3min Resources
	- [ ] 145. What Is A Module? | 11min Resources
	- [ ] 146. Module Pattern | 13min
	- [ ] 147. Module Pattern Pros and Cons | 5min
	- [ ] 148. CommonJS, AMD, UMD | 10min
	- [ ] 149. ES6 Modules | 9min Resources
	- [ ] 150. Section Review | 2min
- [ ] Section 11: Error Handling 00/08 | 43min
	- [ ] 151. Section Overview | 1min Resources
	- [ ] 152. Errors In JavaScript | 9min Resources
	- [ ] 153. Try Catch | 10min Resources
	- [ ] 154. Async Error Handling | 13min Resources
	- [ ] 155. Async Error Handling 2 | 4min Resources
	- [ ] 156. Exercise: Error Handling | 1min Resources
	- [ ] 157. Extending Errors | 5min Resources
	- [ ] 158. Section Review | 1min
