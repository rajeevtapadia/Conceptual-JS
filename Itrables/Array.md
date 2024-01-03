### Array.at(index)
Its similar to `arr[i]` but supports negative values to access array in reverse order.

### Using Array as Stack
Useful methods are:
- `Array.pust(element)` : return the index at which element is added
- `Array.pop()`: returns the popped element

### Using Array as Queue
Useful methods are:
- `Array.shift()` : removes and returns the first element in the Array.
- `Array.unshitf(element)` : adds element to beginning of array.

NOTE: Queue operations are slower as they require more memory operations

### Internal Working of Array
Internally JS arrays are special kind of object.
Hence `arr[age] = 20` will not give any error. But the array optimizations don't work here.
So array shouldn't be misused in the following way: 
- Add a non-numeric property like `arr.test = 5`.
- Make holes, like: add `arr[0]` and then `arr[1000]` (and nothing between them).
- Fill the array in the reverse order, like `arr[1000]`, `arr[999]` and so on.

### Loops over Array
1. The usual `for` loop
```javascript
let arr = ["Apple", "Orange", "Pear"];
for (let i = 0; i < arr.length; i++) {
  alert( arr[i] );
}
```
2. `for..of` loop
```javascript
let fruits = ["Apple", "Orange", "Plum"];
// iterates over array elements
for (let fruit of fruits) {
  alert( fruit );
}
```
3. `for..in` loop (as arrays are objects)
```javascript
let arr = ["Apple", "Orange", "Pear"];

for (let key in arr) {
  alert( arr[key] ); // Apple, Orange, Pear
}
```
NOTE: `for..in` is optimized for general objects and also loops over non-numeric properties too, so it shouldn't be used with Arrays.

### `Array.length` is writable!
Increasing `Array.length` does nothing while decreasing it truncates the array.
So, the simplest way to clear the array is: `arr.length = 0;`

### `Array.toString()`
`toString` method that returns a comma-separated list of elements.
Arrays do not have `Symbol.toPrimitive`, neither a viable `valueOf`, they implement only `toString` conversion
```javascript
alert( [] + 1 ); // "1"
alert( [1] + 1 ); // "11"
alert( [1,2] + 1 ); // "1,21"
```

### `Array.splice()`
Deletes from `start` removes `deleteCount` elements and then inserts `elem1, ..., elemN` at their place. Returns the array of removed elements.
```javascript
arr.splice(start[, deleteCount, elem1, ..., elemN])
```

### `Array.slice()`
Simpler version of `Array.splice()`
```javascript
arr.slice([start], [end])
```

### `Array.concat()`
```javascript
arr.concat(arg1, arg2...)
```
arg1, arg2... argN can be array or primitive value.
If arraylike objects are passed as an arg, it will be added as a whole
```javascript
let arr = [1, 2];

let arrayLike = {
  0: "something",
  length: 1
};

alert( arr.concat(arrayLike) ); // 1,2,[object Object]
```
Unless the array-like object has a special `Symbol.isConcatSpreadable` property, then it’s treated as an array by `concat` and its elements are added instead
```javascript
let arr = [1, 2];

let arrayLike = {
  0: "something",
  1: "else",
  [Symbol.isConcatSpreadable]: true,
  length: 2
};

alert( arr.concat(arrayLike) ); // 1,2,something,else
```

### `Array.forEach()`
return value of the function is ignored
```javascript
arr.forEach(function(item, index, array) {
  // ... do something with item
});
```

### `Array.filter(fn)`
It return the array of element for which function `fn` evaluates to true
```javascript
let results = arr.filter(function(item, index, array) {
  // if true item is pushed to results and the iteration continues
  // returns empty array if nothing found
});
```

### `Array.map(fn)`
It calls the function for each element of the array and returns the array of results.
```javascript
let result = arr.map(function(item, index, array) {
  // returns the new value instead of item
});
```

### `Array.from(obj[, mapFn, thisArg])`
