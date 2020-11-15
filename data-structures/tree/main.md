---
description: >-
A tree is a data structure composed of nodes.
---

# Tree

A tree is a data structure composed of nodes.

- Each tree has a root node.
- The root node has zero or more child nodes.
- Each child node has zero or more child nodes, and so on.
- The tree cannot contain cycles. (That's a [graph](graph.md))

```javascript
class Node {
  constructor(value) {
    this.value = value;
  }
}

class Tree {
  constructor(rootValue) {
    if (rootValue) this.root = new Node(rootValue);
    else this.root = null;
  }

  depthFirstSearch(value) {
    let stack = [this.root];
    while (stack.length) {
      let node = stack.pop();
      if (node.value === value) return node;

      if (!node.children) continue;

      for (let i = node.children.length - 1; i >= 0; i--)
        stack.push(node.children[i]);

      return node;
    }
    return null;
  }

  breadthFirstSearch(value) {
    let queue = [this.root];
    while (queue.length) {
      for (let i = 0; i < queue.length; i++) {
        let node = queue.shift();
        if (node.value === value) {
          return node;
        }
        if (node.children && node.children.length) {
          for (let i = 0; i < children.length; i++) queue.push(children);
        }

        if (node.left) {
          queue.push(tree[node.left]);
        }
        if (node.right) {
          queue.push(tree[node.right]);
        }
      }
    }
    return null;
  }
}
```
