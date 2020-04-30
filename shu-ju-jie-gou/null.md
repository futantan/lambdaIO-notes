# null

typeof null === "object"

（其实这已经被设计和维护JavaScript的委员会TC39认定是一个错误。在逻辑上，你可以认为null是一个空的对象指针，所以结果为“object”，但这还是很令人困惑。）

```text
undefined == null // true
undefined === null // false
```

判断是否为 null `xxx === null`

当判断是否为 null 时，永远使用恒等号 ===，因为 == 无法区分 null 和 undefined

