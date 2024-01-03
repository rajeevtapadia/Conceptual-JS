Object properties, besides a **`value`**, have three special attributes (so-called “flags”):

- **`writable`** – if `true`, the value can be changed, otherwise it’s read-only.
- **`enumerable`** – if `true`, then listed in loops, otherwise not listed.
- **`configurable`** – if `true`, the property can be deleted and these attributes can be modified, otherwise not.

## `getOwnPropertyDescriptor`
- It gets all the property flags
```javascript
let descriptor = Object.getOwnPropertyDescriptor(obj, propertyName);
```

## `defineProperty`
- Can be used to set flags to `propertyName`
- If `propertyName` doesn't exits it will get created
```javascript
Object.defineProperty(obj, propertyName, descriptor)
```

