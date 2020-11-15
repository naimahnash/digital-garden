---
description: >-
A linked list is a one way data structure of linked nodes. If it is two-way it is called a doubly linked list.

---

# Linked List

```javascript
class LLNode {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

export class LinkedList {
  constructor() {
    this.head = null;
    this.size = 0;
  }

  add(value) {
    let newNode = new LLNode(value);
    if (!this.head) {
      this.head = newNode;
    } else {
      let node = this.head;
      while (node.next) {
        node = node.next;
      }
      node.next = newNode;
    }
    this.size++;
  }

  isEmpty() {
    return this.size === 0;
  }
}
```

```javascript
class DLLNode extends LLNode {
  constructor(value) {
    this.value = value;
    this.next = null;
    this.prev = null;
  }
}

export class DoubleLinkedList {
  constructor() {
    this.head = null;
    this.size = 0;
  }

  add(value) {
    let newNode = new DLLNode(value),
      prevNode = null;
    if (!this.head) {
      this.head = newNode;
    } else {
      let node = this.head;
      while (node.next) {
        prevNode = node;
        node = node.next;
      }
      node.next = newNode;
      node.prev = prevNode;
    }
    this.size++;
  }

  pop() {
    let node = this.head,
      nodeToReturn = null,
      prevNode = null;
    while (node.next) {
      prevNode = node;
      node = node.next;
    }
    nodeToReturn = node;
    prevNode.next = null;
    this.size--;
    return nodeToReturn;
  }
}
```
