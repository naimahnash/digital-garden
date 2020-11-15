# Binary Tree

A binary tree is a tree in which each node has up to two children.
A node is called a "leaf" node if it has no children.

```javascript
class BinaryNode extends Node {
  constructor(value) {
    super(value);
    this.left = null;
    this.right = null;
  }
}

/**
 * @description A binary tree is a tree in which each node has up to two children.
 * A node is called a "leaf" node if it has no children.
 */
class BinaryTree extends Tree {
  constructor(rootValue) {
    super();
    if (rootValue) {
      this.root = new BinaryNode(rootValue);
    } else this.root = null;
  }

  getRootNode() {
    return this.root;
  }
}
```

## Binary Search Tree

A binary search tree is a binary tree in which for each node, its left descendants are less than or equal to the current node, which is less than the right descendants.

- Note that this inequality must be true for all of a node's descendants, not just its immediate children.

### Balanced vs. Unbalanced

Balancing a tree does not mean the left and right subtrees are exactly the same size, but means something more like not terribly imbalanced:

It's balanced enough to ensure O(log n) times for insert and find, but it's not necessarily as balanced as it could be.

Two common types of balanced trees are red-black trees and AVL trees.

### Complete Binary Trees

A complete binary tree is a binary tree in which every level of the tree is fully filled, except for perhaps the last level. To the extent that the last level is filled, it is filled left to right.

### Full Binary Trees

A full binary tree is a binary tree in which every node has either zero or two children. That is, no nodes have only one child.

### Perfect Binary Trees

A perfect binary tree is one that is both full and complete. All leaf nodes will be at the same level, and this level has the maximum number of nodes.

- Note that perfect trees are rare in interviews and in real life, as a perfect tree must have exactly _2k - 1_ nodes (where _k_ is the number of levels). In an interview, do not assume a binary tree is perfect.

## Binary Tree Traversal

### In-order Traversal

In-order traversal means to "visit" (often, print) the left branch, then the current node, and finally, the right branch.

- When performed on a binary search tree, it visits the nodes in ascending order (hence the name "in-order").

### Pre-order Traversal

Pre-order traversal visits the current node before its child nodes (hence the name "pre-order").

- In a pre-order traversal, the root is always the first node visited.

### Post-order Traversal

Post-order traversal visits the current node after its child nodes (hence the name "post-order").

- In a post-order traversal, the root is always the last node visited.

```javascript
/**
 * @description A binary search tree is a binary tree in which every node fits a specific ordering property:
 *  all left descendents <= n < all right descendents.
 *  This must be true for each node n.
 */
class BinarySearchTree extends BinaryTree {
  constructor(rootValue) {
    super(rootValue);
  }

  insert(value) {
    const newNode = new BinaryNode(value);
    if (this.root === null) this.root = newNode;
    else {
      let current = this.root;
      let parent;
      while (true) {
        parent = current;
        if (value < current.value) {
          current = current.left;
          if (current === null) {
            parent.left = newNode;
            break;
          }
        } else {
          current = current.right;
          if (current === null) {
            parent.right = newNode;
            break;
          }
        }
      }
    }
    return this;
  }
  /**
   * @description the left branch, then the current node, and finally, the right branch.
   * @param {Node} node
   * @param {function} visit is a callback function (can print or push to array or something)
   */
  inOrderTraversal(node, visit) {
    while (node != null) {
      this.inOrderTraversal(node.left, visit);
      visit(node); //either printing or doing some other kind of something.
      this.inOrderTraversal(node.right, visit);
      break;
    }
    return;
  }

  /**
   * @description visits the current node before its child nodes
   * @param {Node} node
   * @param {function} visit is a callback function (can print or push to array or something)
   */
  preOrderTraversal(node, visit) {
    while (node != null) {
      visit(node); //either printing or doing some other kind of something.
      this.preOrderTraversal(node.left, visit);
      this.preOrderTraversal(node.right, visit);
      break;
    }
  }

  /**
   * @description visits the current node after its child nodes.
   * @param {Node} node
   * @param {function} visit is a callback function (can print or push to array or something)
   */
  postOrderTraversal(node, visit) {
    while (node != null) {
      this.postOrderTraversal(node.left, visit);
      this.postOrderTraversal(node.right, visit);
      visit(node); //either printing or doing some other kind of something.
      break;
    }
  }
}
```
