# Binary Search Tree

### Binary Search Tree

A binary tree is a Binary Search Tree if:

* left < root < right
* applies to all subtrees (all children/grand-kid of left < root < all children/grand-kid of right)

[Deletion of node](https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/141/basic-operations-in-a-bst/1025/):

Case 1. If the target node has _**no child**_, we can simply remove the node.\
Case 2. If the target node has _**one child**_, we can use its child to replace itself.\
Case 3. If the target node has _**two children**_, replace the node with its in-order successor or predecessor node and delete that node.

Implementation of BST:

```python
class BSTNode:
    def __init__(self, val=None):
        self.left = None
        self.right = None
        self.val = val
​
    def insert(self, val):
        if not self.val:
            self.val = val
            return

        if self.val == val:
            return

        if val < self.val:
            if self.left:
                self.left.insert(val)
            else:
                self.left = BSTNode(val)
        else:
            if self.right:
                self.right.insert(val)
            else:
                self.right = BSTNode(val)
​
    def get_min(self):
        current = self
        while current.left is not None:
            current = current.left
        return current.val
​
    def get_max(self):
        current = self
        while current.right is not None:
            current = current.right
        return current.val
​
    def delete(self, val):
        if self == None:
            return self
        if val < self.val:
            if self.left:
                self.left = self.left.delete(val)
            return self
        if val > self.val:
            if self.right:
                self.right = self.right.delete(val)
            return self
        # Case 2: replace with only child
        if self.right == None:
            return self.left
        if self.left == None:
            return self.right
        # Case 3: replace with in-order successor or predecessor node
        min_larger_node = self.right
        while min_larger_node.left:
            min_larger_node = min_larger_node.left
        self.val = min_larger_node.val
        self.right = self.right.delete(min_larger_node.val)
        return self
​
    def search(self, val):
        if self.val == val:
            return self
        if self.left and self.val > val:
            return self.search(self.left, val)
        if self.right and self.val < val:
            return self.search(self.right, val)
        return None
```

### References:

Theory:

* [https://www.programiz.com/dsa/binary-search-tree](https://www.programiz.com/dsa/binary-search-tree)

Implementation:

* Ultimate guide: [https://blog.boot.dev/computer-science/binary-search-tree-in-python/](https://blog.boot.dev/computer-science/binary-search-tree-in-python/)
* Basic operations implementation practice: [https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/141/basic-operations-in-a-bst/](https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/141/basic-operations-in-a-bst/)

