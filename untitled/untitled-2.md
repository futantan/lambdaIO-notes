# Untitled

函数具有对象的全部特征，完全可以将函数当做对象来用。只是多了一个`()`操作，用来执行函数的逻辑。

```text
function Sing() {
  console.log(Sing.author + ":" + Sing.poem);
}
Sing.author = 'Alice';
Sing.poem = 'To be or not to be...';
Sing(); // Alice:To be or not to be...
```

上述代码中，`Sing` 函数（或者说对象）动态添加了 author 和 poem 属性

