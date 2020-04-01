# Function

最后一个是可执行的代码，之前是参数，参数也可以用逗号分隔

```text
var addFunction = new Function('num1', 'num2', 'return num1 + num2');
/* Alternately, a single comma-separated string with arguments can be
  the first parameter of the constructor, with the function body following. */
var timesFunction = new Function('num1,num2', 'return num1 * num2');
console.log(addFunction(2,2),timesFunction(2,2)); 
// logs '4 4'
```

