# Untitled 1

function Person\(name\) { this.name = name; } Person.prototype.sayName = function \(\) { console.log\(this.name\); } Person.prototype.toString = function \(\) { return "\[Person " + this.name + "\]"; }

实例变量定义在构造函数中 所有的方法都定义在构造器的原型上

对于多个实例方法，可能想要一起定义，如下：

```text
function Person(name) {
  this.name = name;
}
Person.prototype = {
  sayName: function() {
    console.log(this.name);
  },
  toString: function() {
    return "[Person " + this.name + "]";
  }
};
```

但是有一个副作用需要注意。使用对象字面形式改写原型对象改变了构造函数的属性，因此它现在指向Object而不是Person。这是因为原型对象具有一个constructor属性，这是其他对象实例所没有的。当一个函数被创建时，它的prototype属性也被创建，且该原型对象的constructor属性指向该函数。当使用对象字面形式改写原型对象Person.prototype时，其constructor属性将被置为泛用对象Object。为了避免这一点，需要在改写原型对象时手动重置其constructor属性，如下例。

```text
function Person(name) {
  this.name = name;
}
Person.prototype = {
  constructor: Person, // important!
  sayName: function() {
    console.log(this.name);
  },
  toString: function() {
    return "[Person " + this.name + "]";
  }
};
```

`[[Prototype]]`属性只是包含了一个指向原型对象的指针，任何对原型对象的改变都立即反映到所有引用它的对象实例上。这意味着你给原型对象添加的新成员都可以立即被所有已经存在的对象实例使用

可以随时改变原型对象的能力在封印对象和冻结对象上有一个十分有趣的后果。当你在一个对象上使用Object.seal\(\)或Object.freeze\(\)时，完全是在操作对象的自有属性。你无法添加自有属性或改变冻结对象的自有属性，但仍然可以通过在原型对象上添加属性来扩展这些对象实例

