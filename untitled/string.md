# string

strings are **immutable** value

下面的规则对 `Number` `Boolean` 也适用

避免使用 `new String('xxx')` ，应该使用字面量，或者 `String('xx')`

```text
var stringObject = new String('foo');
console.log(stringObject); 
// logs foo {0 = 'f', 1 = 'o', 2 = 'o'}
console.log(typeof stringObject); // logs 'object'

var stringObjectWithOutNewKeyword = String('foo'); 
// without new keyword
console.log(stringObjectWithOutNewKeyword); // logs 'foo'
console.log(typeof stringObjectWithOutNewKeyword); // logs 'string'

var stringLiteral = 'foo';
console.log(stringLiteral); // logs foo
console.log(typeof stringLiteral); // logs 'string'
```

