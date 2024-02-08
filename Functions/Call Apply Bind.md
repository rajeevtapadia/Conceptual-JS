# Call Apply Bind

## Call
```javascript
func.call(context, arg1, arg2, ...)
```
With call method we can give custom value to `this` keyword while calling a function

## Apply
```javascript
func.apply(context, arguments)
```
- It runs the func setting this=context and using an array-like object args as the list of arguments.
- The only syntax difference between call and apply is that call expects a list of arguments, while apply takes an array-like object with them.

So these two calls are almost equivalent:
```javascript
func.call(context, ...args);
func.apply(context, args);
```

## Bind
The problem `bind()` solves: Losing `this`
```javascript
let user = {
  firstName: "John",
  sayHi() {
    alert(`Hello, ${this.firstName}!`);
  }
};

setTimeout(user.sayHi, 1000); // Hello, undefined!
```
#### Solution 1: Wrapper
```javascript
setTimeout(() => user.sayHi(), 1000); // Hello, John!
```
Vulnerability: `user` object might change before `setTimeout` triggers and it can call to wrong object

#### Solution 2: `bind`
```javascript
let bound = func.bind(context, [arg1], [arg2], ...);
```
`bind` method can bind the value of this as well as arguments

Hence the solution to above problem will be
```javascript
let user = {
  firstName: "John",
  sayHi() {
    alert(`Hello, ${this.firstName}!`);
  }
};

setTimeout(user.sayHi.bind(user), 1000); // Hello, John!
```