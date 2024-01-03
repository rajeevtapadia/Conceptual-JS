`Map` – is a collection of keyed values.
Difference between Map and Object is Map allows keys of any type (any primitive or even object)

Methods and properties:
- `new Map([iterable])` – creates the map, with optional `iterable` (e.g. array) of `[key,value]` pairs for initialization.
- `map.set(key, value)` – stores the value by the key, returns the map itself.
- `map.get(key)` – returns the value by the key, `undefined` if `key` doesn’t exist in map.
- `map.has(key)` – returns `true` if the `key` exists, `false` otherwise.
- `map.delete(key)` – removes the element by the key, returns `true` if `key` existed at the moment of the call, otherwise `false`.
- `map.clear()` – removes everything from the map.
- `map.size` – returns the current element count.

NOTE: Maps shouldn't be accessed as `map[key]`


### Iteration over Map
For looping over a `map`, there are 4 methods:

- `map.keys()` – returns an iterable for keys,
- `map.values()` – returns an iterable for values,
- `map.entries()` – returns an iterable for entries `[key, value]`, it’s used by default in `for..of`.
- `map.forEach()`

NOTE: iteration over `Map` is always in insertion order

### Map from Object
When a `Map` is created, we can pass an array (or another iterable) with key/value pairs
```javascript
let map = new Map([
  ['1',  'str1'],
  [1,    'num1'],
  [true, 'bool1']
]);
```
Or if we have a plain object we can use the `Object.entries(obj)`
```javascript
let obj = {
  name: "John",
  age: 30
};

let map = new Map(Object.entries(obj));
```