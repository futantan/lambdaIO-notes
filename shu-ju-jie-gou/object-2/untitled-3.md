# prototype

几乎所有的函数都有prototype属性，它可以被修改或替换。该prototype属性被自动设置为一个新的继承自Object.prototype的泛用对象，该对象有一个自有属性constructor。实际上，JavaScript引擎为你做了下面的事情。

```text
// you write this
function YourConstructor() {
  // initialization
}
// JavaScript engine does this for you behind the scenes
YourConstructor.prototype = Object.create(Object.prototype, {
  constructor: {
    configurable: true,
    enumerable: true,
    value: YourConstructor,
    writable: true
  }
});

// inherits from Rectangle
function Square(size) {
  this.length = size;
  this.width = size;
}
Square.prototype = Object.create(Rectangle.prototype, {
  constructor: {
    configurable: true,
    enumerable: true,
    value: Square,
    writable: true
  }
});
Square.prototype.toString = function () {
  return "[Square " + this.length + "x" + this.width + "]";
};
```

在这个版本的代码中，Square.prototype被改写为一个新的继承自Rectangle.prototype的对象，而Rectangle构造函数没有被调用。这意味着，你不再需要担心不加参数调用构造函数会导致的错误。除此之外，这段代码和\[\[对象继承\]\]的代码行为完全一致。原型对象链完好无缺，所有的Square对象实例都继承自Rectan-gle.prototype且其constructor属性也都在同样的地方被重置。

