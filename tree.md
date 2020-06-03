# Binary tree

+ [Symmetric Tree](#symmetric-tree)

## Symmetric Tree

https://leetcode.com/problems/symmetric-tree/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        path = []
        def euler(node):
            if not node: path.append(None); return
            path.append(node.val)
            euler(node.left)
            path.append(node.val)
            euler(node.right)
            path.append(node.val)
        euler(root)
        return path == path[::-1]

```