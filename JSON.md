## `JSON.stringify(value [, replacer, space])`
- value: A value to be encoded in to string
- replacer: Array of properties to encode or a mapping function
- space: Amount of space used for a tab

Used to convert objects into JSON-string.

`JSON.stringify()` skips JS specific object properties like:
1. Function properties (methods)
2. Symbolic keys and values
3. Properties which store undefined

Its limitation: Objects should now contain circular references
```javascript
let room = {
  number: 23
};

let meetup = {
  title: "Conference",
  participants: ["john", "ann"]
};

meetup.place = room;       // meetup references room
room.occupiedBy = meetup; // room references meetup

JSON.stringify(meetup); // Error: Converting circular structure to JSON
```

### Using Replacer Function
The circular reference problem can be solve by using a replacer function.
This function is called recursively on each key, value pair
```javascript
alert( JSON.stringify(meetup, function replacer(key, value) {
  alert(`${key}: ${value}`);
  return (key == 'occupiedBy') ? undefined : value;
}));
```


## `JSON.parse(str, [reviver])
- str: JSON string to parse
- reviver: Optional `function(key, value)` that will be called over each key, value

### Using Reviver Function
If `JSON.parse()` is called on a string with a `Date` object, the date will be converted to a string. To get an actual `Date` object we have to use a Reviver function 
```javascript
let str = '{"title":"Conference","date":"2017-11-30T12:00:00.000Z"}';

let meetup = JSON.parse(str, function(key, value) {
  if (key == 'date') return new Date(value);
  return value;
});

alert( meetup.date.getDate() ); // now works!
```