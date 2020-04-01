# this

The `this` keyword, passed to **all** functions, is a reference to the object that contains the function.

Just remember that, in general, `this` is used inside of functions to refer to the object the function is contained within, as opposed to the function itself \[exceptions include using the new keyword or call\(\) and apply\(\)\].

Even though normal functions have no use for this, it still exists as a special variable whose value is always **the global objec**t \(window in browsers;\)\(in strict mode is undefined \)

## 改变 this 的三种方式

* call
* apply
* bind \(bind 在修改 this 的同时，也可以 partially apply argument\)

[call & apply](JavaScript/this/call%20apply.md)

Another application of this, is generic interface functions, which can be used in mixins or traits.

In the following example, the Movable interface contains generic function move, which expects the users of this mixin to implement \_x, and \_y properties:

```text
// Generic Movable interface (mixin).
let Movable = {
  /**
   * This function is generic, and works with any
   * object, which provides `_x`, and `_y` properties,
   * regardless of the class of this object.
   */
  move(x, y) {
    this._x = x;
    this._y = y;
  },
};

let p1 = new Point(1, 2);
// Make `p1` movable.
Object.assign(p1, Movable);
// Can access `move` method.
p1.move(100, 200);
console.log(p1.getX()); // 100
```

