# Untitled 4

六种：

[string](JavaScript/Untitled%204/string.md)

[number](JavaScript/Untitled%204/number.md)

[boolean](JavaScript/Untitled%204/boolean.md)

[null](JavaScript/Untitled%204/null.md)

[undefined](JavaScript/Untitled%204/undefined.md)

[symbol](JavaScript/Untitled%204/symbol.md)

**All** primitives are **immutable**

其他编程语言用栈储存原始类型，用堆储存引用类型，JavaScript则完全不同：它使用一个变量对象追踪变量的生存期。

尽管原始类型拥有方法，但它们不是对象。

当读取字符串、数字或布尔值时，原始封装类型将被自动创建。 注: 然后自动销毁。类似于 auto boxing

一个对象在条件判断语句中总被认为是 true，无论该对象的值是不是等于 false。

为了让原始类型看上去更像引用类型，JavaScript提供了3种原始封装类型：String、Number和Boolean。JavaScript会在背后创建这些对象使得你能够像使用普通对象那样使用原始值，但这些临时对象在使用它们的语句结束时就立刻被销毁。

