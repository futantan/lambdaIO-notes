# call apply

[Function.prototype.call\(\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

```text
// apply() and call() pattern
var greet = {
  runGreet: function(){
    console.log(this.name,arguments[0],arguments[1]);
  }
}

var cody = {name:'cody'};
var lisa = {name:'lisa'};

// invoke the runGreet function as if it were inside of the cody object
greet.runGreet.call(cody,'foo','bar'); // logs 'cody foo bar'

// invoke the runGreet function as if it were inside of the lisa object
greet.runGreet.apply(lisa, ['foo','bar']); // logs 'lisa foo bar'
```

Notice the _**difference**_ between `call()` and `apply()` in _how parameters are sent_ to the function being invoked

[ECMAScript 2015 Language Specification - ECMA-262 6th Edition](https://www.ecma-international.org/ecma-262/6.0/#sec-function.prototype.call)

