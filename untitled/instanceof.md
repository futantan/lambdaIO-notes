# instanceof

任何时候判断一个对象是否是Object 实例时，它都将返回 true，因为所有对象都继承自 Object\(\) 构造函数。

instanceof **只适用**于构造函数创建返回的_复杂对象和实例_。

```text
'foo' instanceof String             // false
String('foo') instanceof String     // false
new String('foo') instanceof String // true
```

