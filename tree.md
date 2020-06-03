# Binary tree

+ [Invert Binary Tree](#invert-binary-tree)

## Invert Binary Tree

https://leetcode.com/problems/invert-binary-tree/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def invertTree(self, root):
        if root:
            root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)
            return root

```