# for in - object

`for in` 用来遍历 `object` 中非 `Symbol` 的可枚举的属性。

需要注意的是，添加到 Object.prototype 之上的属性，会被遍历到。

* `for-in` 循环同时也会遍历原型属性而 
* `Object.keys()` 只返回自有（实例）属性。

```javascript
var foo = {a: 1, b: 2, c: 3};

for (var property in foo) {
  console.log(property);
}
// a b c
```

**不应该用来遍历数组，原因：** 

1. 顺序不能保证 
2. 原型上的属性也会包含

```javascript
const arr = [1, 2, 3];

for (el in arr) {
  console.log(el); 
  // 1, 2, 3
}

Array.prototype.foo = "hello"

for (el of arr) {
  console.log(el); 
  // ---> 1, 2, 3
}

for (el in arr) {
  console.log(el); 
  // ---> 1, 2, 3, "hello"
}
```

