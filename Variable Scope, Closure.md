## About `let` & `const`
Variable declared in a block `{...}` is local to that block.
This holds for plain `{...}` block as well as if, for, while, etc.

## Lexical Environment
- A variable is a key in a special object called Lexical Environment
- Every block has its own Lexical Environment
- Whenever a variable is accessed it is first searched in the inner lexical environment
   and if not found it will be searched in outer environment.
- Important thing to note is that every function remember the lexical environment is was created in.

## Closure
**Closure allows a function to retain access to the variables from its outer (enclosing) scope even after the outer function has finished execution.**
```javascript
function makeCounter() {
  let count = 0;

  return function() {
    return count++;
  };
}

let counter = makeCounter();
```
- Here the the returned function remembers its outer environment which contains `count`. Hence even after `makeCounter` returns we can still access `count` through `counter()`

## About `var`
- Variables declared with `var` are either function-scoped or global-scope, they can be seen through blocks.
```javascript
if (true) {
  var test = true; // use "var" instead of "let"
}
alert(test); // true, the variable lives after if
```

- `var` can tolerate redeclaration
```javascript
var user = "Pete";
var user = "John"; // this "var" does nothing (no error thrown)
// ...it doesn't trigger an error

alert(user); // John
```

- `var` variables can be declared below their use
This is because `var` declarations are processed when the function starts.
This is called 'Hoisting' (raising).
```javascript
function sayHi() {
  phrase = "Hello"; // (*)
  if (false) {
    var phrase;
  }
  alert(phrase);
}
sayHi();
```
NOTE: here even if the `if` block doesn't get executed the declaration is already processed.