Accessor properties are represented by “getter” and “setter” methods. In an object literal they are denoted by `get` and `set`:

```javascript
let user = {
  name: "John",
  surname: "Smith",

  get fullName() {
    return `${this.name} ${this.surname}`;
  },

  set fullName(value) {
    [this.name, this.surname] = value.split(" ");
  }
};

// set fullName is executed with the given value.
user.fullName = "Alice Cooper";
alert(user.fullName)
```

## Accessor Descriptors
For accessor properties, there is no `value` or `writable` flag.
- **`get`** – a function without arguments, that works when a property is read,
- **`set`** – a function with one argument, that is called when the property is set,
- **`enumerable`** – same as for data properties,
- **`configurable`** – same as for data properties.