# var

```javascript
var a = 123        // 1
b = 123            // 2
function hello() {
	msg = "hello"    // 3
}
hello()
msg === "hello"
```

使用 var 和不使用 var 这两种方式的区别：

* 如果是在 global scope，没有区别
* 如果是在函数作用域中，没有 var 的会一直在作用域链中查找，直至找到，没有找到的话会创建一个

不推荐使用 var

