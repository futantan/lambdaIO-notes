# AMD CommonJS

> AMD\(最流行的实现是RequireJS\)和CommonJS是两个相互竞争的标准，均可以定义JavaScript模块。除了语法和原理的区别之外，主要的区别是AMD的设计理念是明确基于浏览器，而CommonJS的设计是面向通用JavaScript环境（如Node.js服务端），而不局限于浏览器。
>
> AMD有以下几项优点。

1. 自动处理依赖，我们无需考虑模块引入的顺序。
2. 异步加载模块，避免阻塞。
3. 在同一个文件中可以定义多个模块

> 由于CommonJS要求一个文件是一个模块，文件中的代码就是模块的一部分。因此，不需要使用立即执行函数来包装变量。在模块中定义的变量都是安全地包含在当前模块中，不会泄露到全局作用域。
>
> CommonJS具有两个**优势**。 1. 语法简单。只需定义module.exports属性，剩下的模块代码与标准JavaScript无差异。引用模块的方法也很简单，只需要使用require函数。 2. CommonJS是Node.js默认的模块格式，所以我们可以使用npm上成千上万的包。
>
> CommonJS最大的**缺点**是不显式地支持浏览器。浏览器端的JavaScript不支持module变量及export属性，我们不得不采用浏览器支持的格式打包代码，可以通过Browserify（[http://browserify.org/）或RequireJS（http://requirejs.org/docs/commonjs.html）来实现](http://browserify.org/）或RequireJS（http://requirejs.org/docs/commonjs.html）来实现)

为了解决 AMD 和 CommonJS 兼容问题

> 一种解决方案是采用UMD（Universal Module Definition, [https://github.com/umdjs/umd），这种模式的语法有点复杂，它同时支持AMD和CommonJS。](https://github.com/umdjs/umd），这种模式的语法有点复杂，它同时支持AMD和CommonJS。)
>
> ES6模块结合了CommonJS与AMD的优点，具体如下。 ● 与CommonJS类似，ES6模块语法相对简单，并且基于文件（每个文件就是一个模块）。 ● 与AMD类似，ES6模块支持异步模块加载。

