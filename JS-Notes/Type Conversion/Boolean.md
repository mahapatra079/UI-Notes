# Boolean

let b = 123
console.log(Boolean(b)); // true

let x = null
console.log(Boolean(x)); // false

let y = undefined
console.log(Boolean(y)); // false

let i = []
console.log(Boolean(i)); // true

let z = true
console.log(Boolean(z)); // true

let q = '@@'
console.log(Boolean(q)); // true

let a = ''
console.log(Boolean(a)); // false

let p = NaN
console.log(Boolean(p)); // false

let h = 1
console.log(Boolean(h)); // true

let k = 0
console.log(Boolean(k)); // false

Conclusion

- `Boolean()` function converts a value to a boolean. It can convert various types of
   values, including numbers, strings, null, undefined, arrays, and more, into their boolean representation.

- For example, `Boolean(123)` will return `true`, while `Boolean(0)` will return `false`, and `Boolean('')` will return `false`.

- In general, the following values are considered falsy in JavaScript:
  - `false`
  - `0`
  - `''` (empty string)
  - `null`
  - `undefined`
  - `NaN`

- All other values are considered truthy, meaning they will evaluate to `true` when converted to a boolean.