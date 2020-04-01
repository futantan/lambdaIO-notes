# Untitled 6

Recursion: JavaScript technically supports recursion, but most functional languages have a feature called proper tail calls. Proper tail calls are a language feature which allows recursive functions to reuse stack frames for recursive calls.

Without proper tail calls, a call stack can grow without bounds and cause a stack overflow. JavaScript technically proper tail calls in the ES6 specification. Unfortunately, only one of the major browser engines enabled it as a default feature, and the optimization was partially implemented and then subsequently removed from Babel \(the most popular standard JavaScript compiler, used to compile ES6 to ES5 for use in older browsers\).

Bottom line: It still isn’t safe to use recursion for large iterations — even if you’re careful to call the function in the tail position.

