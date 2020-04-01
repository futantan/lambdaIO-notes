# Babel

[Custom operator](JavaScript/Babel/Custom%20operator.md)

![Babel/Untitled.png](../../.gitbook/assets/untitled%20%281%29.png)

[LOLCODE-to-JavaScript compiler babel macro - A geek with a hat](https://swizec.com/blog/lolcode-to-javascript-compiler-babel-macro/swizec/9083)

## Learn

[jamiebuilds/babel-handbook](https://github.com/jamiebuilds/babel-handbook/blob/master/translations/en/user-handbook.md)

[jamiebuilds/babel-handbook](https://github.com/jamiebuilds/babel-handbook/blob/master/translations/en/plugin-handbook.md)

## 工具

[AST explorer](https://astexplorer.net/)

[JointJS - JavaScript diagramming library - Demos.](https://resources.jointjs.com/demos/javascript-ast)

## 文章

[https://www.toptal.com/javascript/write-code-to-rewrite-your-code](https://www.toptal.com/javascript/write-code-to-rewrite-your-code)

[https://www.sitepoint.com/understanding-asts-building-babel-plugin/](https://www.sitepoint.com/understanding-asts-building-babel-plugin/)

[https://www.kenneth-truyers.net/2016/05/27/writing-custom-eslint-rules/](https://www.kenneth-truyers.net/2016/05/27/writing-custom-eslint-rules/)

* 👍[转向JavaScript系列 AST in Modern JavaScript - 简书](https://www.jianshu.com/p/82894a71376e)
* [Babel是如何读懂JS代码的](https://zhuanlan.zhihu.com/p/27289600)
* [ ] [用 js 写一个简单的编译器](https://github.com/jamiebuilds/the-super-tiny-compiler)
* [ ] [Writing custom EsLint rules](https://www.kenneth-truyers.net/2016/05/27/writing-custom-eslint-rules/)
* [ ] [Refactoring With Codemods and jscodeshift \| Toptal](https://www.toptal.com/javascript/write-code-to-rewrite-your-code)
* [ ] [The State of Babel · Babel](https://babeljs.io/blog/2016/12/07/the-state-of-babel)
* [ ] [Understanding ASTs by Building Your Own Babel Plugin — SitePoint](https://www.sitepoint.com/understanding-asts-building-babel-plugin/)
* [ ] [JavaScript Program Slicing with SliceJS · GitHub](https://gist.github.com/kentcdodds/5a13a838cb2c915a2fbcd780c5c0de50#file-learning-code-md)
* [ ] [JointJS - JavaScript diagramming library - Demos.](http://resources.jointjs.com/demos/javascript-ast)
* [ ] [GitHub - acornjs/acorn: A small, fast, JavaScript-based JavaScript parser](https://github.com/acornjs/acorn)!!!! 使用试试
* [ ] [https://github.com/estree/estree](https://github.com/estree/estree)
* [ ] [Jison](http://zaa.ch/jison/)

## Action

* [ ] [babel-plugin-transform-remove-console - npm](https://www.npmjs.com/package/babel-plugin-transform-remove-console) -&gt; 看源码
* [ ] jscodeshift Codemod recast ast-types

[babel-core: add options for different parser/generator by hzoo · Pull Request \#3561 · babel/babel · GitHub](https://github.com/babel/babel/pull/3561)

社区中有各种AST parser实现

* 早期有uglifyjs和esprima
* espree, 基于esprima，用于eslint,[Introducing Espree, an Esprima alternative](https://link.zhihu.com/?target=https%3A//eslint.org/blog/2014/12/espree-esprima)
* acorn,号称是相对于esprima性能更优， [Acorn: yet another JavaScript parser](https://link.zhihu.com/?target=http%3A//marijnhaverbeke.nl/blog/acorn.html)
* babylon,出自acorn,用于babel
* babel-eslint,babel团队维护的，用于配合使用ESLint, [GitHub - babel/babel-eslint: ESLint using Babel as the parser.](https://link.zhihu.com/?target=https%3A//www.google.com/url%3Fsa%3Dt%26rct%3Dj%26q%3D%26esrc%3Ds%26source%3Dweb%26cd%3D1%26cad%3Drja%26uact%3D8%26ved%3D0ahUKEwj69NX_lpbYAhXsyVQKHfczBPUQFggoMAA%26url%3Dhttps%253A%252F%252Fgithub.com%252Fbabel%252Fbabel-eslint%26usg%3DAOvVaw0x-Lq143pwLICbowM-n1HZ)

[kentcdodds/babel-plugin-macros](https://github.com/kentcdodds/babel-plugin-macros)

[Sweet.js - Hygienic Macros for JavaScript](https://www.sweetjs.org/)

* The parser parses the code string into a data representational structure called AST \(abstract syntax tree\) using `[@babel/parser](http://github.com/babel/babel/tree/master/packages/babel-parser)`.
* The AST is being manipulated by pre-defined plug-ins which use`[@babel/traverse](http://github.com/babel/babel/tree/master/packages/babel-traverse)`.
* The AST is being transformed back into code using `[@babel/generator](http://github.com/babel/babel/tree/master/packages/babel-generator)`.

  [The Super Tiny Compiler - README.md](https://the-super-tiny-compiler.glitch.me/)

[Write Plugin](JavaScript/Babel/Write%20Plugin.md)

[Babel Document\(progress\)](JavaScript/Babel/Babel%20Document%20progress.md)

* [ ] [https://en.wikipedia.org/wiki/Visitor\_pattern](https://en.wikipedia.org/wiki/Visitor_pattern)
* [ ] what is Source map? [https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/)

