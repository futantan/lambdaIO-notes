# Preventing Object Modification

## Preventing Extensions

使用 `Object.preventExtensions()` 来创建不可扩展的对象（无法添加新的属性）

## Sealing Objects

对象封印是创建不可扩展对象的第二种方法。一个被封印的对象是不可扩展的且其所有属性都不可配置。这意味着不仅不能给对象添加新属性，也不能删除属性或改变其类型（从数据属性变成访问器属性或相反）。如果一个对象被封印，只能读写它的属性。 可以用`Object.seal()`方法来封印一个对象。

## Freezing Objects

如果一个对象被冻结，则不能在其上添加或删除属性，不能改变属性类型，也不能写入任何数据属性。简而言之，被冻结对象是一个数据属性都为只读的被封印对象。被冻结对象无法解冻。可以用`Object.freeze()`来冻结一个对象，用`Object.isFrozen()`来判断一个对象是否被冻结，

