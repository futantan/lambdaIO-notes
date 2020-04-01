# 作用域

### 作用域种类

1. function
2. global
3. eval

只有上述三种作用域，不存在 `block` 作用域。\(ES6 中的 let 其实是 block 作用域\)

JavaScript will declare any variables lacking a var declaration \(even those contained in a function or encapsulated functions\) to be in the global scope instead of the intended local scope.

Scope 决定于函数定义的时候，而不是运行的时候，这被称为 lexical scoping 也是 closure 可以捕获变量的原因。 The scope chain is created before you invoke a function. Because of this, we can create closures.

### 函数的作用域提升

```text
assert(typeof fun === "function", "fun is a function even thought its definition isn't reached yet!")
assert(typeof muFunExp === "undefined", "But we cannot access function expressions");
assert(typeof myArrow === "undefined", "Nor arrow functions");

function fun () {}
var myFunExpr = function();
var myArrow = (x) => x;

assert(typeof fun === "function", "We access the function");
var fun = 3;
assert(typeof fun === "number", "Now we access the number");
function fun() {}
assert(typeof fun === "number", "Still a number"); // 仍然指向数字
```

