# Object create

As we can see, a default object is actually _never empty_ — it always inherits _something_ from the `Object.prototype`.

To create a _prototype-less dictionary_, we have to explicitly set its prototype to `null`:

```text
// Doesn't inherit from anything. 
let dict = Object.create(null); 
console.log(dict.toString); // undefined

Object.create({}) // 会继承 Object 拥有一些方法
```

