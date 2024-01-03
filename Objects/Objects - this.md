To access object, a method can use `this` keyword.
The value of `this` is the object "before dot"

### `this` is not bound in JS

`this` can be used in any function even if it is not a method to an object
```javascript
function sayHi() {
  alert( this.name );    // no error here
}
```

value of this is evaluated during runtime
if `sayHi` function is called as a method `this` will bind to the corresponding object
else calling `sayHi()` without an object `this === undefined`

### Effect of "use strict" on `this`

In strict mode: `this === undefined`
In non-strict mode: `this === global object`
`window` in case of browser

### Arrow functions have no `this`

Arrow functions don’t have their “own” `this`. If we reference `this` from such a function, it’s taken from the outer “normal” function.
```javascript
user = {
    name: 'rajeev',
    bimbim: () => {
        console.log(this.name);    // undefined
        const blyad = () => console.log(this.name)    
        blyad();    //undefined
    },
    fuck: function() {
        console.log(this.name)    // rajeev
        const blyad = () => console.log(this.name)
        blyad();    // rajeev
    },
}

user.bimbim();
user.fuck();
```