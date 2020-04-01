# Iteration protocol

[Iteration protocols](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol)

There are two protocols: The [iterable protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol) and the [iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol).

## The iterable protocol

The _iterable_ protocol allows JavaScript objects to define or customize their iteration behavior, such as what values are looped over in a [for..of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of) construct. Some built-in types are [built-in iterables](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#Built-in_iterables) with a default iteration behavior, such as [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) or [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map), while other types \(such as [Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) \) are not.

In order to be _iterable_, an object must implement the _@@iterator_ method, meaning that the object \(or one of the objects up its [prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Inheritance_and_the_prototype_chain) \) must have a property with a _@@iterator_ key which is available via constant [Symbol.iterator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/iterator):

Property Value `[Symbol.iterator]` A zero arguments function that returns an object, conforming to the [iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol).

Whenever an object needs to be iterated \(such as at the beginning of a `for..of` loop\), its `@@iterator` method is called with no arguments, and the returned _iterator_ is used to obtain the values to be iterated.

## The iterator protocol

The _iterator_ protocol defines a standard way to produce a sequence of values \(either finite or infinite\).

An object is an iterator when it implements a `*next()*` method with the following semantics:

Property Value `next`

A zero arguments function that returns an object with two properties:

* `done` \(boolean\)
  * Has the value `true` if the iterator is past the end of the iterated sequence. In this case `value` optionally specifies the /return value/ of the iterator. The return values are explained [here](http://www.2ality.com/2013/06/iterators-generators.html#generators-as-threads).
  * Has the value `false` if the iterator was able to produce the next value in the sequence. This is equivalent of not specifying the `done` property altogether.
* `value` - any JavaScript value returned by the iterator. Can be omitted when `done` is `true`. The `next` method always has to return an object with appropriate properties including `done` and `value`. If a non-object value gets returned \(such as `false` or `undefined` \), a [TypeError](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError) \(“iterator.next\(\) returned a non-object value”\) will be thrown.

Some iterators are in turn iterables:

```text
var someArray = [1, 5, 7];
var someArrayEntries = someArray.entries(); someArrayEntries.toString(); // "[object Array Iterator]"
someArrayEntries === someArrayEntries[Symbol.iterator](); // true
```

## Examples using the iteration protocols

A [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) is an example of a built-in iterable object:

```text
var someString = 'hi';
typeof someString[Symbol.iterator]; // "function"
```

`String`’s [default iterator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/@@iterator) returns the string’s code points one by one:

```text
var iterator = someString[Symbol.iterator]();
iterator + ''; // "[object String Iterator]" iterator.next(); // { value: "h", done: false }
iterator.next(); // { value: "i", done: false }
iterator.next(); // { value: undefined, done: true }
```

Some built-in constructs, such as the [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator), use the same iteration protocol under the hood:

```text
[...someString] // ["h", "i"]
```

We can redefine the iteration behavior by supplying our own `@@iterator`:

```text
var someString = new String('hi');           
// need to construct a String object explicitly to avoid auto-boxing

someString[Symbol.iterator] = function() {
  return { // this is the iterator object, returning a single element, the string "bye"
    next: function() {
      if (this._first) {
        this._first = false;
        return { value: 'bye', done: false };
      } else {
        return { done: true };
      }
    },
    _first: true
  };
};
```

Notice how redefining `@@iterator` affects the behavior of built-in constructs that use the iteration protocol:

```text
[...someString]; // ["bye"]
someString + ''; // "hi"
```

## Iterable examples

## Built-in iterables

`String`, `Array`, `TypedArray`, `Map` and `Set` are all built-in iterables, because each of their prototype objects implements an `@@iterator` method.

## User-defined iterables

We can make our own iterables like this:

```text
var myIterable = {};
myIterable[Symbol.iterator] = function* () { 
  yield 1; 
  yield 2; 
  yield 3;
};
[...myIterable]; // [1, 2, 3]
```

## Built-in APIs accepting iterables

There are many APIs that accept iterables, for example: [Map\(❲iterable❳\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map), [WeakMap\(❲iterable❳\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap), [Set\(❲iterable❳\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) and [WeakSet\(❲iterable❳\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakSet):

```text
var myObj = {};
new Map([[1, 'a'], [2, 'b'], [3, 'c']]).get(2);               
// "b"
new WeakMap([[{}, 'a'], [myObj, 'b'], [{},'c']]).get(myObj); 
// "b"
new Set([1, 2, 3]).has(3);                               
// true
new Set('123').has('2');                                 
// true
new WeakSet(function* () {
    yield {};
    yield myObj;
    yield {};
}()).has(myObj);                                         
// true
```

Also see [Promise.all\(iterable\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all), [Promise.race\(iterable\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/race), and [Array.from\(\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from).

## Syntaxes expecting iterables

Some statements and expressions expect iterables, for example the [for-of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)loops, [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator), [yield\*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield*), and [destructuring assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment):

```text
for(let value of ['a', 'b', 'c']){ 
  console.log(value);
}
// "a"
// "b"
// "c" 

[...'abc']; // ["a", "b", "c"] 
function* gen() { 
  yield* ['a', 'b', 'c'];
} 
gen().next(); // { value:"a", done:false } 
[a, b, c] = new Set(['a', 'b', 'c']);
a // "a"
```

## Non-well-formed iterables

If an iterable’s `@@iterator` method doesn’t return an iterator object, then it’s a non-well-formed iterable. Using it as such is likely to result in runtime exceptions or buggy behavior:

```text
var nonWellFormedIterable = {}
nonWellFormedIterable[Symbol.iterator] = () => 1
[...nonWellFormedIterable] // TypeError: [] is not a function
```

## Iterator examples

## Simple iterator

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
var it = makeIterator(['yo', 'ya']); console.log(it.next().value); // 'yo'
console.log(it.next().value); // 'ya'
console.log(it.next().done); // true
```

## Infinite iterator

```text
function idMaker() { 
  var index = 0; 
  return { 
    next: function(){ 
      return {value: index++, done: false}; 
    } 
  };
} 
var it = idMaker(); 
console.log(it.next().value); // '0'
console.log(it.next().value); // '1'
console.log(it.next().value); // '2'
// ...
```

## With a generator

```text
function* makeSimpleGenerator(array) { 
  var nextIndex = 0; 
  while (nextIndex < array.length) { 
    yield array[nextIndex++]; 
  }
} 
var gen = makeSimpleGenerator(['yo', 'ya']); console.log(gen.next().value); // 'yo'
console.log(gen.next().value); // 'ya'
console.log(gen.next().done); // true 

function* idMaker() { 
  var index = 0; 
  while (true) yield index++;
} 
var gen = idMaker(); 
console.log(gen.next().value); // '0'
console.log(gen.next().value); // '1'
console.log(gen.next().value); // '2'
// ...
```

## With ECMAScript 6 class

```text
class SimpleClass { 
  constructor(data) { 
    this.index = 0; 
    this.data = data; 
  } 
  [Symbol.iterator]() { 
    return { 
      next: () => { 
        if (this.index < this.data.length) { 
          return {
            value: this.data[this.index++], 
            done: false
          }; 
        } else { 
          this.index = 0; //If we would like to iterate over this again without forcing manual update of the index 
          return {done: true}; 
        } 
      } 
    } 
  };
} 
const simple = new SimpleClass([1,2,3,4,5]); 
for (const val of simple) { 
  console.log(val); //'0' '1' '2' '3' '4' '5' 
}
```

## Is a generator object an iterator or an iterable?

A [generator object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator) is both, iterator and iterable:

```text
var aGeneratorObject = function* () {
    yield 1;
    yield 2;
    yield 3;
}();
typeof aGeneratorObject.next;
// "function", because it has a next method, so it's an iterator
typeof aGeneratorObject[Symbol.iterator];
// "function", because it has an @@iterator method, so it's an iterable
aGeneratorObject[Symbol.iterator]() === aGeneratorObject;
// true, because its @@iterator method returns itself (an iterator), so it's an well-formed iterable
[...aGeneratorObject];
// [1, 2, 3]
```

## See also

* For more information on ES2015 generators, see [the function\* documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*).

