# Binary Tree

Each node has two children (left and right) and node value.

### Types of Binary Trees

1.  #### Full Binary Tree / Proper Binary Tree

    every parent node node has either two or no children
2.  #### Perfect Binary Tree

    every node has exactly two child nodes + all the leaf nodes are at the same level
3.  #### Complete Binary Tree

    full binary tree, but with two major differences

    1. Every level must be completely filled, except possibly the lowest one
    2. All the leaf elements must lean towards the left.
    3. The last leaf element might not have a right sibling i.e. a complete binary tree doesn't have to be a full binary tree.
4.  #### Balanced Binary Tree

    difference between the height of the left and the right subtree for each node is either 0 or 1
5.  #### Skewed Binary Tree

    the tree is either dominated by the left nodes or the right nodes
6.  #### Degenerate or Pathological Tree

    tree having a single child either left or right

### Traversals:

**In-order**: left -> root -> right

<div align="left"><figure><img src="../../.gitbook/assets/image (9).png" alt="" width="262"><figcaption></figcaption></figure></div>

\[4,2,6,5,7,1,3,9,8]

[https://leetcode.com/problems/binary-tree-inorder-traversal/](https://leetcode.com/problems/binary-tree-inorder-traversal/)

```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack = []
        ans = []
        while stack or root:
            while root:
                stack += [root]
                root = root.left
            root = stack.pop()
            ans += [root.val]
            root = root.right
        return ans

```

**Post-order**: left -> right -> root

<div align="left"><figure><img src="../../.gitbook/assets/image (10).png" alt="" width="262"><figcaption></figcaption></figure></div>

\[4,6,7,5,2,9,8,3,1]

[https://leetcode.com/problems/binary-tree-postorder-traversal/description/](https://leetcode.com/problems/binary-tree-postorder-traversal/description/)

```python
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack = [root]
        ans = []
        while stack:
            curr = stack.pop()
            if curr:
                # pre-order, but we want to pop right first
                ans += [curr.val]
                stack += [curr.left] 
                stack += [curr.right]
        return ans[::-1]

```

**Pre-order**: root -> left -> right

<div align="left"><figure><img src="../../.gitbook/assets/image (11).png" alt="" width="262"><figcaption></figcaption></figure></div>

\[1,2,4,5,6,7,3,8,9]

[https://leetcode.com/problems/binary-tree-preorder-traversal/](https://leetcode.com/problems/binary-tree-preorder-traversal/)

```python
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack = [root]
        ans = []
        while stack:
            curr = stack.pop()
            if curr:
                ans += [curr.val]
                stack += [curr.right]
                stack += [curr.left]
        return ans

```

### References&#x20;

Theory:

* [https://www.programiz.com/dsa/binary-tree](https://www.programiz.com/dsa/binary-tree)

Implimentation:&#x20;

* same link

### Good questions on Binary Trees <a href="#good-questions-on-heaps" id="good-questions-on-heaps"></a>
