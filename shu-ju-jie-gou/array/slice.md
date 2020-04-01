# slice

[Array.prototype.slice\(\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

`slice` does **not** alter the original array. It returns a shallow copy of elements from the original array. Elements of the original array are copied into the returned array as follows:

```text
arr.slice([begin[, end]])
// begin 默认为 0
// end 默认为 length
arr.slice() 等同于 [...arr]
```

两个参数均可以为**负数**

## Array-like objects

convert Array-like objects / collections to a new Array

```text
// way 1
function list() {
  return Array.prototype.slice.call(arguments);
}
// way 2
function list() {
  return [].slice.call(arguments);
}
// way 3
var unboundSlice = Array.prototype.slice;
var slice = Function.prototype.call.bind(unboundSlice);

function list() {
  return slice(arguments);
}
```

