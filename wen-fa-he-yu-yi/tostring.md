# toString

一旦`valueOf()`返回的是一个引用而不是原始值的时候，就会回退调用 `toString()` 方法 

另外，当 JavaScript 期望一个字符串时，也会对原始值隐式调用 `toString()`   
例如，当加号操作符的一个边是一个字符串时，另一边会被自动转换成字符串。

* 如果另一边是一个原始值，会自动被转换成一个字符串表达（例如，true 转换成 "true"）
* 如果另一边是一个**引用值**，则会调用`valueOf()`。如果valueOf\(\)返回一个引用值，则调用toString\(\)

