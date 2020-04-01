# Untitled

This converts a value to a boolean and _ensures a boolean type_.

```text
"foo"      =    "foo"
!"foo"     =    false
!!"foo"    =    true
```

If `foo.bar` is passed through, then it may not be 0 but some other falsy value. See the following truth table:

> Truth Table for javascript

```text
''        ==   '0'           // false
0         ==   ''            // true
0         ==   '0'           // true
false     ==   'false'       // false
false     ==   '0'           // true
false     ==   undefined     // false
false     ==   null          // false
null      ==   undefined     // true
" \t\r\n" ==   0             // true
```

Javascript also gets really weird when it comes to NaN values. And this is the only case I can think of off the top of my head where !! would behave differently to ===.

```text
NaN   ===  NaN     //false
!!NaN === !!NaN    //true

// !!NaN is false
```

