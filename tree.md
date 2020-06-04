# Binary tree

+ [Kth Smallest Element in a BST](#kth-smallest-element-in-a-bst)

## Kth Smallest Element in a BST

https://leetcode.com/problems/kth-smallest-element-in-a-bst/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def in_order_traversal(self, root):
        if not root: return
        self.in_order_traversal(root.left)
        self.list.append(root.val)
        self.in_order_traversal(root.right)

    def kthSmallest(self, _root, k):
        """
        :type _root: TreeNode
        :type k: int
        :rtype: int
        """
        root = _root
        if not root: return 0

        self.list = []
        self.in_order_traversal(root)

        return self.list[k - 1]

```