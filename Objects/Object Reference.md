	Difference between objects vs primitives is that objects are stored and copied 'by reference'

#### Comparison by Reference
Two objects are only equal if they are the same object i.e. both reference to same memory location 
Two objects are NOT equal even If they have same set of key: value pairs
```javascript
let a = {};
let b = a; // copy the reference

alert( a == b ); // true, both variables reference the same object
alert( a === b ); // true
```

#### Cloning a Object
- `Object.assign`
```javascript
const clone = Object.assign(dest, ...sources)
```
	- The first argument `dest` is a target object.
	- Further arguments is a list of source objects.
	- return value is the cloned object

- `{ ...spread }`
	- spread operator can be used to shallow copy a object

- `structuredClone`
```javascript
const clone = structuredClone(object)
```
	- it also supports circular refrences
	- objects with functions are not supported