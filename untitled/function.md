# function

[arguments](arguments.md)

[函数与对象](untitled-2.md)

[arrow function](JavaScript/function/arrow%20function.md)

[Function](function-4.md)

对熟悉面向对象编程的同学来说，可能会认为 `Function`，`Method`和`Constructor` 是三个不同的东西，而在 JS 中，这三种都是 Function 的不同形式。

* 函数是最容易鉴别的**引用类型**，因为对函数使用typeof操作符时，返回值是“function”。
* 使函数不同于其他对象的决定性特点是函数存在一个被称为`[[Call]]`的内部属性。
* 函数**期望的**参数个数保存在函数的 length 属性中。
* JavaScript 函数其实根本没有签名，因此也**不存在重载**。

  const obj = { abc: function \(\) {} }; // 也可以写成下面这样 const obj = { abc\(\) { } }

> `obj.abc()` 相当于 `obj.abc.call(obj, x, y)`

除了显式传入的参数，每个函数会有两个额外的参数信息： `this` `arguments`

* arguments
* caller
* length
* name
* prototype
* **proto**

