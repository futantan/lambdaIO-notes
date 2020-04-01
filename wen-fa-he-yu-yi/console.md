# console

```javascript
const a = { name: 'alice', age: 10 }
console.log(a)
a.name = 'bob';

// 这个时候，如果打开之前的 log，会发现 a.name 是 'bob'
```

> WebKit的 `console.log` 由于表现出异步行为而让很多开发者惊诧不已。
>
> WebKit 的 `console.log` 并没有立即拍摄对象快照，相反，它只存储了一个指向对象的引用，然后在代码返回事件队列时才去拍摄快照。Node 的 `console.log` 是另一回事，它是严格同步的，

## API

* console.log
* console.error
* console.warn
* console.info
* console.group
* console.table
* console.count,
* console.time
* console.timeEnd
* console.trace
* console.assert

