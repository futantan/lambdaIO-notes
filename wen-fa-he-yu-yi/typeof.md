# typeof

`typeof` 是运算符，所以后面加不加括号都可以

```javascript
typeof null          // object!!
typeof undefined     // undefined 
typeof 'abc'         // string
typeof String('abc') // string

typeof [] // 'object'
typeof {} // 'object'
typeof new String('abc')                      // object！！
typeof new Array('foo', 'bar')                // object
typeof new Function('x', 'y', 'return x * y') // function
typeof function() {}                          // function
typeof new RegExp('\\bt[a-z]+\\b')            // object
```

函数是最容易鉴别的引用类型，因为对函数使用 typeof 操作符时，返回值总是 `"function"`。

还有一个不错的判断类型的方法，就是Object.prototype.toString，我们可以利用这个方法来对一个变量的类型来进行比较准确的判断

```javascript
Object.prototype.toString.call(1)         // "[object Number]"
Object.prototype.toString.call('hi')      // "[object String]"
Object.prototype.toString.call({a:'hi'})  // "[object Object]"
Object.prototype.toString.call([1,'a'])   // "[object Array]"
Object.prototype.toString.call(true)      // "[object Boolean]"
Object.prototype.toString.call(() => {})  // "[object Function]"
Object.prototype.toString.call(null)      // "[object Null]"
Object.prototype.toString.call(undefined) // "[object Undefined]"
Object.prototype.toString.call(Symbol(1)) // "[object Symbol]"
```

### null

对于所有非函数的**引用类型**，typeof 返回 `"object"`。需要特别注意的是： `typeof null === 'object'`

为什么会出现这种情况呢？因为在 JS 的最初版本中，使用的是 32 位系统，为了性能考虑使用低位存储了变量的类型信息，000 开头代表是对象，然而 null 表示为全零，所以将它错误的判断为 object 。虽然现在的内部类型判断代码已经改变了，但是对于这个 Bug 却是一直流传下来。

js 在底层存储变量的时候，会在变量的机器码的低位1-3位存储其类型信息

* 000：对象
* 010：浮点数
* 100：字符串
* 110：布尔
* 1：整数

但是, 对于 `undefined` 和 `null` 来说，这两个值的信息存储是有点特殊的。

* `null`：所有机器码均为0
* `undefined`：用 −2^30 整数来表示

### isObjectLike

lodash `isObjectLike` 源码：

```javascript
function isObjectLike(value) {
  return typeof value == 'object' && value !== null
}
```



