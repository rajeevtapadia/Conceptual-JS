Spread syntax can be used to make functions with variable number of args.

- When `...` is at the end of function parameters, it’s “rest parameters” and gathers the rest of the list of arguments into an array.
```javascript
function sumAll(...args) { // args is the name for the array
  let sum = 0;
  for (let arg of args) sum += arg;
  return sum;
}

alert( sumAll(1, 2, 3) ); // 6
```

- When `...` occurs in a function call or alike, it’s called a “spread syntax” and expands an array into a list.
```javascript
let arr = [3, 5, 1];

alert( Math.max(...arr) ); // 5 (spread turns array into a list of arguments)
```