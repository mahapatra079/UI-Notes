# Number

let b = "123";
let num1 = parseInt("123");
console.log(num1) // 123

let a = " ";
let num2 = parseInt(" ");
console.log(num2) // NaN

let x = "null";
let num3 = parseInt("null")
console.log(num3) // NaN

let y = "undefined";
let num4 = parseInt("undefined")
console.log(num4) // NaN

let d = "boolean";
let num5 = parseInt("boolean")
console.log(num5) // NaN

let i = "[]";
let num6 = parseInt("[]")
console.log(num6) // NaN

let z = "true";
let num7 = parseInt("true")
console.log(num7) // NaN

let q = '@@';
let num8 = parseInt("@@")
console.log(num8) // NaN

let t = null;
let num9 = parseInt(null)
console.log(num9) // NaN

let s = undefined;
let num10 = parseInt(undefined)
console.log(num10) // NaN

let o = [];
let num11 = parseInt([])
console.log(num11); // NaN

let n = true
let num12 = parseInt(true)
console.log(num12); // NaN

let p = NaN
let num13 = parseInt(NaN)
console.log(num13); // NaN


Conclusion 

- `parseInt()` function converts a string to an integer. If the string cannot be converted to a number, 
   it returns `NaN` (Not a Number).

- When `parseInt()` is given an empty string or a string with only whitespace, it returns `NaN`.

- When `parseInt()` is given a string that starts with a valid number followed by non-numeric characters,
  it will parse the valid number and ignore the rest. For example, `parseInt("123abc")` will return `123`.

