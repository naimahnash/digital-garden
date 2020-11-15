---
description: >-
  A trie (sometimes called a prefix tree) is a variant of an n-ary tree in which characters are stored at each node. Each path down the tree may represent a word.
---

# Trie

A trie (sometimes called a prefix tree) is a variant of an n-ary tree in which characters are stored at each node. Each path down the tree may represent a word.

The null nodes are often used to indicate complete words.

A trie can check if a string is a valid prefix in _0(K)_ time, where _K_ is the length of the string.

```javascript
class TrieNode extends Node {
  constructor(value) {
    super(value);
    this.children = {};
  }
}

const TERMINALNODE = "*";

class Trie extends Tree {
  constructor() {
    super();
    this.root = new TrieNode();
  }

  insert(value) {
    let node = this.root;
    for (let char of value) {
      if (!node.children[char]) {
        node.children[char] = new TrieNode(char);
      }
      node = node.children[char];
    }
    node.children[TERMINALNODE] = null;
    return this; //so we can chain inserts
  }
}
```
