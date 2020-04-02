# call apply

```javascript
// apply() and call() pattern
var greet = {
  runGreet: function(){
    console.log(this.name, arguments[0], arguments[1])
  }
}

var cody = {name:'cody'}
var lisa = {name:'lisa'}

// invoke the runGreet function as if it were inside of the cody object
greet.runGreet.call(cody,'foo','bar'); // logs 'cody foo bar'

// invoke the runGreet function as if it were inside of the lisa object
greet.runGreet.apply(lisa, ['foo','bar']); // logs 'lisa foo bar'
```

`call()` 和 `apply()` 的区别在于如何传递参数



