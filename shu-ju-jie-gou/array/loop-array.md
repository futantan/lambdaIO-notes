# loop array

* a `for-of` loop \(ES2015+ only\),
* `Array#forEach` \(spec \| MDN\) \(or its relatives some and such\) \(ES5+ only\),
* a simple old-fashioned `for loop`,
* or `for-in` with safeguards.

_**Don’t**_ use `for-in` unless you use it with safeguards or are at least aware of why it might bite you.

Iterating arrays for-in should be avoided, that statement is meant to _enumerate_ object properties. It shouldn’t be used for array-like objects because: The _order_ of iteration is not guaranteed, the array indexes may not be visited in numeric order. _Inherited_ properties are also enumerated. For example:

```text
Array.prototype.foo = "foo!";
var array = ['a', 'b', 'c'];

for (var i in array) {
  alert(array[i]);
}
```

The above code will alert, “a”, “b”, “c” and “foo!”.

