# Iterators

_一句话解释_

> 提供一个 `next()` 方法，返回一个对象，包含 `done` 和 `value`。

```text
function makeIterator(array) {
  var nextIndex = 0;

  return {
     next: function() {
       return nextIndex < array.length ?
         {value: array[nextIndex++], done: false} :
         {done: true};
    }
  };
}

var it = makeIterator(['yo', 'ya']);
console.log(it.next().value); // 'yo'
console.log(it.next().value); // 'ya'
console.log(it.next().done);  // true
```

