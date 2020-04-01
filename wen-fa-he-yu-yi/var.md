# var

var a = 123 b = 123 function hello\(\) { msg = "hello" } hello\(\) msg === "hello"

这两种方式的区别： If you’re in the global scope then there’s no difference.

If you’re in a function then var will create a local variable, “no var” will look up the scope chain until it finds the variable or hits the global scope \(at which point it will create it\):

