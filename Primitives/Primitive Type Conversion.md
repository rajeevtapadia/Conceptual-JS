- #### String conversion
String() function can be used for conversion
Pretty obvious. `true` becomes `"true"`, `null` becomes `"null"`

- #### Numeric conversion
`Number()` function can be used for conversion
General rule is if `+` operator involves convert to `string`
and `-` is involved convert to `number`
Rules:

| Value | Becomes |
| :------: | :----------: |
| undefined | NaN |
| null |  0 |
| true/false | 1/0 |
| string | whitespaces are removed.<br>if string is empty then `0`, <br>if error then NaN|

- #### Boolean conversion
Boolean() function can be used for conversion.
Rules:

| Value | Becomes |
| :---: | :---: |
| `0`, `null`, `undefined`, `NaN`, `""`<br> (values which are intuitively empty) | `false` |
| any other value | `true` |

NOTE: `"0"` & `" "` are true

#### Comparison operators
while using comparison operator JS converts string to number
```javascript
alert( '2' > 1 ); // true, string '2' becomes a number 2
alert( '01' == 1 ); // true, string '01' becomes a number 1
```