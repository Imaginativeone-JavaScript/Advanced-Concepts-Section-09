## Lesson Taught
async/await

## What I Learned
Syntactic sugar, alternative to the syntax of Promises

	- [ ] 137225 09-05-10 1522 ES8 - Async Await
	  - Built on top of Promises
		- Underneath the hood, an async function is a function that returns a Promise
		- The benefit of async/await is that it makes code easier to read

		## A Promise that looks like this:

		```javascript
		movePlayer(100, 'Left')
			.then(() => movePlayer(400, 'Left'))
			.then(() => movePlayer( 10, 'Right'))
			.then(() => movePlayer(330, 'Left'))
		```

		## Might look like this with async/await

		```javascript
		async function playerStart() {
			// const firstMove = await .then(() => movePlayer(400, 'Left')); 	// pause
			const first  = await .then(() => movePlayer(400, 'Left')); 			// pause
			const second = await .then(() => movePlayer(400, 'Left'));			// pause
			await .then(() => movePlayer( 10, 'Right')); 						// pause
			await .then(() => movePlayer(330, 'Left')); 						// pause
		}
		```

		## Getting data from the web (Promise Version)

		```javascript
        function getDataFromWeb() {
            // fetch() // I get a Promise
            // https://jsonplaceholder.typicode.com/users
            fetch('https://jsonplaceholder.typicode.com/users')
                .then(userAccountResolution => userAccountResolution.json())
                .then(console.log)
        }
		```

		## Getting data from the web (async/await Version)

		```javascript
        function asyncGetWebData() {
            async function fetchUsers() {
                const userAccountResolution = await fetch('https://jsonplaceholder.typicode.com/users')
                const data = await userAccountResolution.json();
                console.log('data', data);
            }
        }
		```

		## Another Example

		```javascript
		const urls = [
			'https://jsonplaceholder.typicode.com/users',
			'https://jsonplaceholder.typicode.com/posts',
			'https://jsonplaceholder.typicode.com/albums'
		]

		const getData = async function() {

			const [users, posts, albums] = await Promise.all(
				urls.map(
					url => fetch(url).then(userAccountResolution => userAccountResolution.json())
				)
			)
			console.log('users',  users);
			console.log('posts',  posts);
			console.log('albums', albums);
		}
		```

		## try/catch Error Handling
		
		```javascript
		const urls = [
			'https://jsonplaceholder.typicode.com/users',
			'https://jsonplaceholde.typicode.com/posts',	// Erroneous URL
			'https://jsonplaceholder.typicode.com/albums'
		]

		const getData = async function() {
			try {
				const [users, posts, albums] = await Promise.all(
					urls.map(
						url => fetch(url).then(userAccountResolution => userAccountResolution.json())
					)
				)
				console.log('users', 	users);
				console.log('posts', 	posts);
				console.log('albums', albums);
			}
			catch(err) {
				console.log('Oops', err);
			}
		}
        ```

	- [ ] 138225 09-06-10 0521 ES9 (ES2018)
	  - Object spread operator

		```javascript
		const animals = {
			tiger: 23,
			lion: 5,
			monkey: 2,
			bird: 40
		}

		// const { tiger, ...nontigers } = animals;
		
		function objectSpread(p1, p2, p3) {
			console.log('p1', p1);	
			console.log('p2', p2);	
			console.log('p3', p3);	
		}

		const { tiger, lion, ...rest } = animals;

		console.log(tiger);
		console.log(rest);

		objectSpread(tiger, lion, rest);
		```

	- [ ] 139225 09-07-10 1111 ES9 (ES2018) - Async (finally)

		## Old Promise Example

		```javascript
        function oldWayOfUsingPromises() {
            const urls = [
                'https://swapi.dev/api/people/1',
                'https://swapi.dev/api/people/2',
                'https://swapi.dev/api/people/3',
                'https://swapi.dev/api/people/4',
            ];

            Promise.all(
                urls.map(
                    url => {
                        return fetch(url).then(characters => characters.json())
                    }
                )
            )
            .then((array) => {
                // throw Error;
                console.log('0', array[0]);
                console.log('1', array[1]);
                console.log('2', array[2]);
                console.log('3', array[3]);
            })
            .catch(err => console.log('please fix this', err))
            .finally(data => console.log('extra', data)) // Run a piece of code, no matter what: email, notfication, etc
        }
		```

		## for/await/of

		```javascript
		function exploreAsyncFor() {
			const urls = [
				'https://jsonplaceholder.typicode.com/users',
				'https://jsonplaceholder.typicode.com/posts',
				'https://jsonplaceholder.typicode.com/albums'
			]

			const getUserAccountInfo = async function() {

                // On the following line, here's what's happening:
                // I have three sets of data that I can access from a remote server.
                // I'm looping through the urls, to set up respective responses for 
                //   information from that server.
				const acctInfoPromises = urls.map((url) => fetch(url) );
                
				for await (let request of acctInfoPromises) {
					const data = await request.json();
					console.log('data', data);
				}

                // This is a PROMISE that a request must be made on.
                const userInfo = acctInfoPromises[0];
                console.log('userInfo', userInfo);

				return acctInfoPromises;
			}
			getUserAccountInfo();
		}
		```

## Thoughts and Questions

Can I use an async function in an event listener?
