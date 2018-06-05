# How to pass arguments to a node.js script

- Starting with npm start
```sh
$ npm run start -- [args]
```

- Passing arguments to a script
```sh
$ node script.js [args]
```

- How to read the passed arguments in the script file
```js
var args = process.argv.slice(2);
```
With this command, all args will be stored in the args array, you can access then by the list index

- **Example**
```sh
$ node script.js this_is_a test
```

script.js
```js
var args = process.argv.slice(2);
console.log(args) // [ 'this_is_a', 'test' ]
```
