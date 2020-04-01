# Thunk

A thunk is another word for a _function_. But it’s not just any old function. It’s a special \(and uncommon\) name for a function that’s returned by another. Like this:

```text
function wrapper_function() {
  // this one is a "thunk" because it defers work for later:
  return function thunk() {   // it can be named, or anonymous
    console.log('do stuff now');
  };
}
```

[What the heck is a 'thunk'?](https://daveceddia.com/what-is-a-thunk/)

[getify/You-Dont-Know-JS](https://github.com/getify/You-Dont-Know-JS/blob/master/async%20%26%20performance/ch4.md#thunks)

