---
description: >-
  A heap is a kind of tree where the values are ordered in ascending or descending order.
---

# Heap

## Min-Heap

A [complete binary tree](#complete-binary-tree) where each node is smaller than its children.

- The root, therefore, is the minimum element in the tree.
  We have two key operations on a min-heap: insert and extracting the minimum.

### Insert

When we insert into a min-heap, we always start by inserting the element at the bottom. We insert at the rightmost spot so as to maintain the complete tree property.

Then, we "fix" the tree by swapping the new element with its parent, until we find an appropriate spot for the element. We essentially bubble up the minimum element.

- This takes _0(log n)_ time, where _n_ is the number of nodes in the heap.

### Extract

First, we remove the minimum element and swap it with the last element in the heap (the bottommost, rightmost element). Then, we bubble down this element, swapping it with one of its children until the min-heap property is restored.

Do we swap it with the left child or the right child? That depends on their values. There's no inherent ordering between the left and right element, but you'll need to take the smaller one in order to maintain the min-heap ordering.

- This algorithm will also take _0(log n)_ time

```javascript
class Heap extends BinarySearchTree {
  constructor(rootValue) {
    super(rootValue);
  }

  insert(value) {}
}
```

## Max-Heap

A [complete binary tree](#complete-binary-tree) where each node is larger than its children.

- The root, therefore, is the maximum element in the tree.
