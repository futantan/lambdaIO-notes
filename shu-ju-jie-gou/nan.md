# NaN

Javascript also gets really weird when it comes to NaN values. And this is the only case I can think of off the top of my head where !! would behave differently to ===.

```text
NaN   ===  NaN     //false
!!NaN === !!NaN    //true

// !!NaN is false
```

