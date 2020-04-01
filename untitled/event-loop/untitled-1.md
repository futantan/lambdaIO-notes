# Untitled 1

[https://www.youtube.com/watch?v=u1kqx6AenYw](https://www.youtube.com/watch?v=u1kqx6AenYw)

[Further Adventures of the Event Loop](https://ejzimmer.github.io/event-loop-talk/)

## Browser

```text
while (true) {
  queue = getNextQueue();
  task = queue.pop();
  execute(task);

  while (microtaskQueue.hasTasks()) {
    doMicrotask();
  }

  if (isRepaintTime()) {
    animationTasks = animationQueue.copyTasks();
    for (task of animationTasks) {
            doAnimationTask(task);
    }
    repaint();
  }
}
```

## node

* No script parsing events
* No pesky user interactions
* No animation frame callbacks
* No rendering pipeline at all

  while \(tasksAreWaiting\(\)\) { queue = getNextQueue\(\); while \(queue.hasTasks\(\)\) { task = queue.pop\(\); execute\(task\);

  ```text
    while (nextTickQueue.hasTasks()) {
      doNextTickTask();
    }

    while (promiseQueue.hasTasks()) {
      doPromiseTask();
    }
  }
  ```

  }

## web worker

* No script tags
* No user interactions
* No DOM manipulation

