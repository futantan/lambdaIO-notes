# PubSub

function PubSub\(\) { this.handlers = \[\]; }

```text
PubSub.prototype.on = function(eventType, handler) {
  if (!(eventType in this.handlers)) {
    this.handlers[eventType] = [];
  }
  this.handlers[eventType].push(handler);
  return this;
}

PubSub.prototype.emit = function(eventType) {
  var handlerArgs = Array.prototype.slice.call(arguments, 1);
  for (var i = 0; i < this.handlers[eventType].length; i++) {
    this.handlers[eventType][i].apply(this, handlerArgs);
  }
  return this;
}

const a = new PubSub();
a.on("hello", () => console.log("get hello"));
a.emit("hello");
```

