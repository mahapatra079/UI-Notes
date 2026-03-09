# String

let b = 123
let str1 = String(b);
console.log(str1) //"123"

let x = null
let str2 = String(x);
console.log(str2) // "null"

let y = undefined
let str3 = String(y);
console.log(str3) // "undefined"

let i = []
let str4 = String(i);
console.log(str4) // " "

let z = true
let str5 = String(z);
console.log(str5) // "true"

let q = "@@"
let str6 = String(q);
console.log(str6) // "@@"

let a = ""
let str7 = String(a);
console.log(str7) //""

let p = NaN
let str8 = String(p);
console.log(str8) // "NaN"

let h = 1
let str9 = String(h);
console.log(str9) //'1'

let k = 0
let str10 = String(k);
console.log(str10) //'0'

Conclusion 

- `String()` function converts a value to a string. It can convert various types of
   values, including numbers, booleans, null, undefined, arrays, and more, into their string representation.

- For example, `String(123)` will return the string "123", while
 `String(null)` will return the string "null", and `String(undefined)` will return the string "undefined".

- When converting an array to a string, it will join the elements of the array with commas.
  For example, `String([1, 2, 3])` will return the string "1,2,3".