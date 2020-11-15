---
description: >-
  A queue is a data structures that holds data that is stored sequentially, and data is added at one end and removed at the other. The queue is FIFO (first in, first out).
---

# Queue

```typescript
// FIFO - first in first out, data structure
class Queue<T> {
  queue: T[];
  constructor(value?) {
    this.queue = [];
    if (value) this.queue.push(value);
  }
  enque(value: T) {
    this.queue.push(value);
    // return this to chain enquing;
    return this;
  }
  deque(): T {
    return this.queue.shift();
  }
  get size() {
    return this.queue.length;
  }
}
```
