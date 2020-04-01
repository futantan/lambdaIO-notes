# for of - Array

`for of` 可以在实现了 `iterable protocol` 的数据类型上进行操作，比如 `Array` 和 `Map`。

`Object` 并_没有_实现`iterable protocol`，所以不能在 `Object` 上使用 `for of`。

```javascript
const str = "hello"
for (s of str) {
  console.log(s); // "h", "e", "l", "l", o"
}

const arr = [1, 2, 3];
for (el of arr) {
  console.log(el); // 1, 2, 3
}

for (el in arr) {
  console.log(el); // 1, 2, 3
}

Array.prototype.foo = "hello"

for (el of arr) {
  console.log(el); // ---> 1, 2, 3
}

for (el in arr) {
  console.log(el); // ---> 1, 2, 3, "hello"
}
```

