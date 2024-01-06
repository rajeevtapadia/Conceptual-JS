A `Promise` servers as a link between producing code and consuming function
```javascript
let promise = new Promise(function(resolve, reject) {
  // executor (the producing code)
});
```
When the executor obtains the result, be it soon or late, doesn’t matter, it should call one of these callbacks:

- `resolve(value)` — if the job is finished successfully, with result `value`.
- `reject(error)` — if an error has occurred, `error` is the error object.

The `promise` object returned by the `new Promise` constructor has these internal properties:

- `state` — Initially `"pending"` then `"fulfilled"` or `"rejected"`
- `result` — initially `undefined` then `value` or `error` 

## Consumers: `.then() .catch() .finally()`
### 1. `.then()`
The first argument of `.then` is a function that runs when the promise is resolved and second when it is rejected
```javascript
promise.then(
  function(result) { /* handle a successful result */ },
  function(error) { /* handle an error */ }
);
```

### 2. `.catch()`
If we are only interested in errors we can use `.then(null, onError)` or `.catch(onError)`
```javascript
promise.catch(function(error) { 
  console.log(error)
})
```

### 3. `.finally()`
- A `finally` handler doesn’t get the outcome of the previous handler (it has no arguments). This outcome is passed through instead, to the next suitable handler.
- If a `finally` handler returns something, it’s ignored.
- When `finally` throws an error, then the execution goes to the nearest error handler.
```javascript
new Promise((resolve, reject) => {
  throw new Error("error");
})
  .finally(() => alert("Promise ready")) // triggers first
  .catch(err => alert(err));  // <-- .catch shows the error
```

NOTE: we can also attach these handlers to settled promises. If the promise is already settled the handler will fire immediately