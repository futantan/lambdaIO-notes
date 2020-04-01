# arguments

由于设计上的问题，`arguments` 并不是一个真的数组，它是一个类似数组的 object！拥有一个 `length` 属性可以使用索引，但是没有数组的其他方法

```text
typeof arguments // object
```

（箭头函数中不存在 arguments）

```text
var abc = function(x,y) {console.log(arguments)}
abc(1, 2)
// [1, 2, callee: ƒ, Symbol(Symbol.iterator): ƒ]
var arrFun = () => {console.log(arguments)}
// error arguments is not defined
```

## 判断是否为 arguments

lodash `isArguments` 源码：

```text
function isArguments(value) {
  return isObjectLike(value) 
    && getTag(value) == '[object Arguments]'
}
```

## callee

A reference to the function currently executing

```text
var foo = function foo() {
 console.log(arguments.callee); // logs foo()
 /* callee could be used to invoke recursively the foo function (e.g., arguments.callee()) */
}();
```

## length

`arguments.length` 返回的是调用函数时，**\*传递的**参数个数_，而\*不是定义_的个数

> The arguments.length property beginning with JavaScript 1.4 is deprecated, and the number of arguments sent to a function can be accessed from the length property of the function object. So, moving forward, you can get the length value by leveraging the callee property to first gain reference to the function being invoked \(i.e., arguments.callee.length\).

## Redefining

`arguments` 可以被修改

```text
var foo = false;
var bar = false;

var myFunction = function(foo, bar) {
   arguments[0] = true;
   bar = true;
   console.log(arguments[0], bar); // logs true true
}

myFunction();
```

## 转换为 `array`

```text
var args = Array.prototype.slice.call(arguments);
var args = [].slice.call(arguments);
// ES2015 way (@@iterator IE 不支持)
var args = Array.from(arguments);
var args = [...arguments];
```

