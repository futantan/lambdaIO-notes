# \_\_proto\_\_ prototype

注意：大部分JavaScript引擎在所有对象上都支持一个名为`__proto__`的属性。该属性使你可以直接读写`[[Prototype]]`属性。Firefox、Safari、Chrome和Node.js都支持该属性，且ECMAScript 6 正在考虑将`__proto__`加入到标准中。

```text
function Foo() {}

(new Foo).__proto__ === Foo.prototype
(new Foo).prototype === undefined
```

`prototype` 只存在于构造函数上。对象实例上没有，有的是 `__proto__`

