# Global object

在浏览器中，使用 `var` 声明的变量会放在 `window` 上。

```text
var a = 123
console.log(window.a) // 123

const b = 123
console.log(window.b) // undefined

let c = 123
console.log(window.c) // undefined
```

可以使用 `this` 来访问 `window`，例如`this.a`

