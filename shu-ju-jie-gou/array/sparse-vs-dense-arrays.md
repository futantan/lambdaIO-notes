# sparse vs dense arrays

[JavaScript: sparse arrays vs. dense arrays](http://2ality.com/2012/06/dense-arrays.html)

In general, arrays in JavaScript are _sparse_ – they can have holes in them, because an array is simply a map from indices to values. This blog post explains how to create _dense_ arrays, arrays without holes.

## Sparse arrays

Creating a sparse array of a given length is simple:

> var a = new Array\(3\); a \[ , , \] a.length 3 a\[0\] undefined

When you iterate over it, you can see that it has no elements. JavaScript skips the holes.

> a.forEach\(function \(x, i\) { console.log\(i+". "+x\) }\); // 不会执行 a.map\(function \(x, i\) { return i }\) \[ , , \]

## Dense arrays

Brandon Benvie recently [mentioned](https://mail.mozilla.org/pipermail/es-discuss/2012-April/022273.html) a trick for creating a dense array on the es-discuss mailing list:

> var a = Array.apply\(null, Array\(3\)\); a \[ undefined, undefined, undefined \]

The above invocation is equivalent to

```text
Array(undefined, undefined, undefined)
```

For many things, there is not much of a difference between this array and the previous sparse array:

> a.length 3 a\[0\] undefined

However, you can now iterate over the elements, e.g. to fill the array with values:

> a.forEach\(function \(x, i\) { console.log\(i+". "+x\) }\); 0. undefined 1. undefined 2. undefined a.map\(function \(x, i\) { return i }\) \[ 0, 1, 2 \]

## One more trick

The email also mentions the following trick:

> Array.apply\(null, Array\(3\)\).map\(Function.prototype.call.bind\(Number\)\) \[ 0, 1, 2 \]

This is roughly the same as

```text
Array.apply(null, Array(3))
  .map( function (x,i,...) { return Number.call(x,i,...) })
```

Note that x is the first parameter of call and specifies the value of this. Number being a function, that value is ignored. I prefer the more explicit variant shown above:

```text
Array.apply(null, Array(3))
  .map(function (x,i) { return i })
```

## Useful in practice?

In practice, creating a dense array in the manner described above will make your code difficult to understand for others. It is thus better to use utility functions such as [\_.range](http://documentcloud.github.com/underscore/#range):

> \_.range\(3\) \[ 0, 1, 2 \]

Combine it with map, in order to fill an array with a given value.

> \_.range\(3\).map\(function \(\) { return "a" }\) \[ 'a', 'a', 'a' \]

