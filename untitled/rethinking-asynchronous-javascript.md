# Rethinking Asynchronous JavaScript

JS 是单线程的，但是可以异步。

如果有个 A1 A2 A3 A4 B1 B2 B3 共 7 个任务，每个任务耗时 1 秒，那么一共需要 7 秒完成。但是可以通过 event loop 的调度，使得这些任务，可以并发执行。

