# Iterables

_一句话解释_

> 可以用 `for...of` 来访问 —&gt; 对象需要提供一个 iterator 方法，key 是 `Symbol.iterator`

```text
var myIterable = {};
myIterable[Symbol.iterator] = function* () {
  yield 1;
  yield 2;
  yield 3;
};

for (let value of myIterable) { 
  console.log(value); 
}
// 1
// 2
// 3

or

[...myIterable]; // [1, 2, 3]
```

