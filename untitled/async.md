# Async

[Rethinking Asynchronous JavaScript](JavaScript/Async/Rethinking%20Asynchronous%20JavaScript.md)

[Promise](promise.md)

[PubSub](pubsub.md)

## Callbacks

**Callbacks** have the following drawbacks:

* Callback hell. It’s easy to end up with lots of nested callbacks when handlinghighly asynchronous code. When that happens, code stops being linear andbecomes hard to reason about. Whole applications end up passed around incallbacks, and they become difficult to maintain and debug.
* Callbacks can run more than once. There’s no guarantee the same callback willbe called only once. Multiple invocations can be hard to detect and can result inerrors and general mayhem in your application.
* Callbacks change error semantics. Callbacks break the traditional try/catchmechanism and rely on the programmer to check for errors and pass them around.
* Concurrency gets increasingly complicated. Combining interdependent results ofmultiple asynchronous operations becomes difficult. It requires us to keep trackof the state of each operation in temporal variables, and then delegate them to thefinal combination operation in the proper order.

## Promises

Promises usually make programs more clear by being closer to synchronous code,reducing the need for nesting blocks and keeping track of less state. Unfortunately, promises are not a silver bullet. They’re an improvement over callbacks, but they have a major shortcoming: they only ever yield a single value.

## Event Emitters

event listeners come with their own set of problems, too

* Events force side effects. Event listener functions always ignore their return values, which forces the listener to have side effects if it wants to have any impact in the world.
* Events are not first-class values. For example, a series of click events can’t be passed as a parameter or manipulated as the sequence it actually is. We’re limited to handling each event individually, and only after the event happens.
* It is easy to miss events if we start listening too late. An infamous example of that is the first version of the streams interface in Node.js, which would often emit its data

  event before listeners had time to listen to it, losing it forever.

> Just syntactic sugar for working with promises

```text
function f() {
  return Promise.resolve('TEST');
}

// asyncF is equivalent to f!
async function asyncF() {
  return 'TEST';
}
```

