# new

function MyFunc\(\) {}; var obj = new MyFunc\(\);

```text
function MyFunc() {};
var obj = {};
MyFunc.call(obj);
```

上述两种方式其实是等价的，也就是说，new 的实现中，先创建了一个对象，然后将其作为 this 传入。

```text
function newOperator(Constr, args) {
  var thisValue = Object.create(Constr.prototype); // (1)
  var result = Constr.apply(thisValue, args);
  if (typeof result === 'object' && result != null) {
    return result; // (2)
  }
  return thisValue;
}
```

In line \(1\), you can see that the prototype of an instance created by a constructor `Constr` is `Constr.prototype`. Line \(2\) reveals another feature of the new operator: you can return an arbitrary object from a constructor and it becomes the result of the new operator. This is useful if you want a constructor to return an instance of a subconstructor

## constructor without new

```text
function Person(name) { 
  this.name = name; 
} 
Person.prototype.sayName = function () { 
  console.log(this.name); 
}; 
// note: missing "new"
var person1 = Person("Nicholas");
// false
console.log(person1 instanceof Person);  
// "undefined"  
console.log(typeof person1);     
// "Nicholas"          
console.log(name);
```

注意这里没有使用 `new` 关键字。调用 `Person` 构造函数的时候

```text
this.name = name;
```

`this` 指向全局，如果是浏览器中则为 window，于是这里就创建了一个在 window 上的全局变量 `name`。（在 strict mode）下会报错。

但是有很多的构造函数，例如 Array，在没有使用 new 操作符的时候，也能够正常工作，这是因为它们被设计成了作用域安全的构造函数。

当用 new 调用一个函数时，this 指向的新创建的对象已经属于该构造函数所代表的自定义类型。也就是说，可以在函数内用 instanceof 来检查自己是否被 new 调用。

```text
function Person(name) { 
  if (this instanceof Person) {            
    // called with "new"       
  } else {            
    // called without "new"       
  }
}
```

于是我们可以写成作用域安全版本的构造函数

```text
function Person(name) { 
  if (this instanceof Person) {
    this.name = name; 
  } else {
    return new Person(name);
  }
}
```

参考 \* JavaScript面向对象精要

