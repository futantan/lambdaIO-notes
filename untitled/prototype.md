# prototype

> Prototype A prototype is a delegation object used to implement prototype-based inheritance.

对象在创建的时候，会获得 prototype。如果没有显式指定，会获得一个默认的 `Object.prototype`。 prototype 可以使用 `__proto__` 和 `Object.create` 来显式指定。

```text
// Base object. 
let point = { 
    x: 10, 
    y: 20, 
}; 
// Inherit from `point` object. 
let point3D = {
    z: 30, 
    __proto__: point, 
}; 
console.log(
    point3D.x, // 10, inherited 
    point3D.y, // 20, inherited 
    point3D.z // 30, own
);
```

任何对象都可作为一个对象的 prototype，（原型继承），prototype 自己也可以有自己的 prototype。这样的一个链，直到 null，叫做原型链。

> Prototype chain A prototype chain is a finite chain of objects used to implement inheritance and shared properties.

![prototype/Untitled.png](../.gitbook/assets/untitled.png)

```text
point3D.__proto__ // point
point3D.__proto__.__proto__ // Object.prototype
point3D.__proto__.__proto__.__proto__ // null
```

如果一个 property 在对象上没有找到，那么会以此在其 prototype 上进行寻找，直到整个原型链结束，如果最终没有找到，会返回 `undefined`。 这种机制在技术上被称为动态派发（dynamic dispatch）或代理（delegation）

> 动态派发发生在运行时，与之相对的，静态派发发生在编译时

```text
// An "empty" object. 
let empty = {}; 
console.log(
    empty.toString, // function, from default prototype 
    empty.x, // undefined 
);
```

如上述代码，一个空对象事实上并不是完全空的。它会从 `Object.prototype` 上继承一些属性。 如果想要创建一个真正空的对象，可以使用如下方式：

```text
// Doesn't inherit from anything. 
let dict = Object.create(null); 
console.log(dict.toString); // undefined
```

动态派发机制允许完全改变继承链

```text
let protoA = {x: 10}; 
let protoB = {x: 20}; 
// Same as `let objectC = {__proto__: protoA};`: 
let objectC = Object.create(protoA); 
console.log(objectC.x); // 10 
// Change the delegate: 
Object.setPrototypeOf(objectC, protoB); 
console.log(objectC.x); // 20
```

尽管 `__proto__` 基本已经成为标准，但是在实践中还是推荐使用 `Object.create`, `Object.getPrototypeOf`, `Object.setPrototypeOf`

所有的对象都继承于 `Object.prototype`

```text
Object.prototype.foo = 'foo';

var myString = 'bar';

// logs 'foo', being found at Object.prototype.foo via prototype chain
console.log(myString.foo);
```

myString 会首先在 `String` 的 `prototype` 上寻找 foo，没有找到之后，在 `Object` 上进行寻找。 添加在 `Object.prototype` 上的属性，会在原型链和 `for in` 中上找到。

