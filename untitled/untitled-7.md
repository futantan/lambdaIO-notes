# Untitled 7

利用 closure

```text
function Ninja() {
  var feints = 0;
  this.getFeints = function() {
    return feints;
  };
  this.feint = function() {
    feints++;
  };
}
```

