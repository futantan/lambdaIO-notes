# Untitled 3

## 对象转基本类型

对象在转换基本类型时，首先会调用 valueOf 然后调用 toString。并且这两个方法是可以重写的。

```text
let a = {
  valueOf() {
    return 0
  }
}
```

当然你也可以重写 Symbol.toPrimitive ，该方法在转基本类型时调用优先级最高。

```text
let a = {
  valueOf() {
    return 0;
  },
  toString() {
    return '1';
  },
  [Symbol.toPrimitive]() {
    return 2;
  }
}
1 + a // => 3
'1' + a // => '12'
```

