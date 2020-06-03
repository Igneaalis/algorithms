# Binary tree

+ [Subtree of Another Tree](#subtree-of-another-tree)

## Subtree of Another Tree

https://leetcode.com/problems/subtree-of-another-tree/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSubtree(self, s, t):
        def traverse_tree(node):
            if not node:
                return None
            return "#{} {} {}".format(node.val, traverse_tree(node.left), traverse_tree(node.right))

        return traverse_tree(t) in traverse_tree(s)

```