# Constructor

构造函数就是用 `new` 操作符调用的普通函数。

可以用 `instanceof` 操作符或直接访问 `constructor` 属性来鉴别对象是被哪个构造函数创建的。每一个函数都具有 `prototype` 属性，它定义了该构造函数创建的所有对象共享的属性。通常，共享的方法和原始值属性被定义在原型对象里，而其他属性都定义在构造函数里。constructor属性实际上被定义在原型对象里供所有对象实例共享。原型对象被保存在对象实例内部的 `[[Prototype]]` 属性中。这个属性是一个引用而不是一个副本。

每个函数都拥有一个 `prototype` 属性，因为 js 没有提供一个方式来区别这个函数是否为构造函数。（首字母大小写只是约定）

> 构造函数的作用 1. 创建实例变量 2. 自动设置 prototype

在引入 `class` 之前，都是像如下这样来使用 constructor 的：

```text
function Letter(number) { 
  this.number = number; 
} 
Letter.prototype.getNumber = function() { 
  return this.number; 
}; 
let a = new Letter(1); 
let b = new Letter(2); 
// ... 
let z = new Letter(26); 
console.log(
  a.getNumber(), // 1 
  b.getNumber(), // 2 
  z.getNumber(), // 26 
);
```

上述的方式，其实就是 `class` 语法糖背后帮我们做的事情。

上述代码中的对象关系图：

[Constructor/untitled](JavaScript/Object/Constructor/untitled)

```text
a.__proto__ === Letter.prototype
Letter.prototype.constructor === Letter
Letter.prototype.__proto__ === Object.prototype
Letter.__proto__ === Function.prototype
Function.__proto__ === Object.prototype
Object.__proto__ === null
```

对象上有的是`__proto__` constructor 上有的是 `prototype`

```text
function Person() {}
var person1 = new Person;
console.log(person1 instanceof Person);     // true
```

对象上会自动获得一个 `constructor`，指向构造函数

## return

大多情况下，我们不需要在构造函数中使用 return

* 如果 return 的是对象，该对象会返回（构造函数创建的对象会被忽略）
* 如果 return 的是基础数据类型，新创建的对象会被返回（显式 return 的东西被忽略）

## 构造函数

构造函数实例都拥有指向其构造函数的 Constructor 属性

```text
console.log([1,2,3].constructor === Array); // true
console.log((new Array()).constructor === Array); // true
```

