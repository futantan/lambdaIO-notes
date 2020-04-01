# void 0

href="javascript:void\(0\)" href="javascript:" // 也会返回 undefined

void\(0\) 其实就是 undefined，_重点在于_：无论void后的表达式是什么，void操作符都会返回undefined. 使用 void 而不是直接使用 undefined 的原因：因为undefined在javascript中不是保留字。例如，可以写出如下代码：

```text
function joke() {
  var undefined = "hello world";
  console.log(undefined); // 会输出"hello world"
}
console.log(undefined); // 输出undefined
```

