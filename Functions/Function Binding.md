```javascript
let bound = func.bind(context, [arg1], [arg2], ...);
```
If we call a method on a object inside `setTimeout`, the values stored in the object may change before execution. This may lead to unintended behaviour.
```javascript
let user = {
  firstName: "John",
  sayHi() {
    alert(`Hello, ${this.firstName}!`);
  }
};

setTimeout(() => user.sayHi(), 1000);

// ...the value of user changes within 1 second
user = {
  sayHi() { alert("Another user in setTimeout!"); }
};

// Another user in setTimeout!
```

## `Function.bind()`
Here we can see even if the `user` object was modified the `bind` method preserved the old object.
```javascript
let user = {
  firstName: "John",
  sayHi() {
    alert(`Hello, ${this.firstName}!`);
  }
};

let sayHi = user.sayHi.bind(user); // (*)

// can run it without an object
sayHi(); // Hello, John!

setTimeout(sayHi, 1000); // Hello, John!

// even if the value of user changes within 1 second
// sayHi uses the pre-bound value which is reference to the old user object
user = {
  sayHi() { alert("Another user in setTimeout!"); }
};
```

## Partial Function
Using the `bind` method we can create new functions by putting default arguments into old ones
eg. `multiply(a, b)` function can be converted to `double(a)` by setting default value of `b = 2`.
```javascript
function mul(a, b) {
  return a * b;
}

let double = mul.bind(null, 2);

alert( double(3) ); // = mul(2, 3) = 6
```
NOTE that here a new function is created without modifying the old function.
