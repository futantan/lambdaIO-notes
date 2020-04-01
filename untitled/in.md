# in

var myObject = {foo: 'value'}; console.log\('toString' in myObject\); // logs true

虽然 `myObject` 的 key 中不包含 `toString` 但是在原型链上是有的，所以 `in` 返回 true。

而 `hasOwnProperty` 不包含继承来的属性。

