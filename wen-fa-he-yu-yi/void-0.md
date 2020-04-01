# void 0

`void(0)` 其实就是 `undefined`

**重点在于**：无论 `void` 后的表达式是什么，void 操作符都会返回 undefined. 使用 void 而不是直接使用 undefined 的原因：因为undefined在javascript中不是保留字。例如，可以写出如下代码：

```javascript
function joke() {
  var undefined = "hello world"
  console.log(undefined)
}
joke()                    // "hello world"
console.log(undefined);   // undefined
```

