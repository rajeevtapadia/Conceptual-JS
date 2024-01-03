## Constructor function

Constructor functions technically are regular functions. There are two conventions though:

1. They are named with capital letter first.
2. They should be executed only with `"new"` operator.

When a function is executed with `new`, it does the following steps:

1. A new empty object is created and assigned to `this`.
2. The function body executes. Usually it modifies `this`, adds new properties to it.
3. The value of `this` is returned.

```javascript
function User(name) {
  // this = {};  (implicitly)

  // add properties to this
  this.name = name;
  this.rizzLord = true;

  // return this;  (implicitly)
}
```

### Constructor mode test: `new.target`

We can check if a function was called with `new` or not
If function was called with `new`: `new.target === constructor function`
else not called with `new`: `new.target === undefined`
```javascript
function User() {
  alert(new.target);
}

User(); // undefined
new User(); // function User { ... }
```

### Return from Constructors

Usually constructors don't have return statement. But if there is a return statement then:
- if return is called with object, then that object is returned instead of `this`
- if return is called with a primitive then is is ignored