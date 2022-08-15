The ES6 syntax for import/export changes the way we've imported and exported the functionalites to and from a given module in nodeJS.

Earlier the syntax in nodeJS used to be:
```
// define export in a file
module.exports = {
	someFunc,
	someFuncAlt
}

//define imports in another file

const { someFunc, someFuncAlt } = require('./filepathabove')
```


With ES6 syntax we can define exports as either named or default export. There an be as many exports as you like but only one default export

```
// filename: randoms.js
const someFunc = (x) => x - 5;
const someFuncAlt = (x) => x + 5;

export {
	someFunc as default,
	someFuncAlt
}

// Here someFunc is the default export and someFuncAlt is a named export
// Note that we can create a named export using following syntax too

export const someFuncNew = (x) => x * 5;

// However we cannot create a default export using this method

export default const someFuncNewest = (x) => x / 5; // this will error out

// So you need to define your function/variable and then export it as default

const someFunctionNewest = (x) => x / 5;

export default someFunctionNewest;

// it is however possible to use the above syntax on a class

export default class User {
	constructor(userName) {
		this.userName = userName;
	}
}

// Also its possible to perform a direct default export on a value but you need to do away with its declaration

export default (x) = x % 5;
```

Following are the imports for the same

```
import someFunc, { someFuncAlt } from "./randoms";

// Note that the import for the default export is outside of the curly braces.
// All the named exports will be imported within the curly braces and the default export will be without the curly braces
```