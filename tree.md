# Binary tree

+ [Validate Binary Search Tree](#validate-binary-search-tree)

## Validate Binary Search Tree

https://leetcode.com/problems/validate-binary-search-tree/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right


class Solution(object):
    def isValidBST(self, _root, first=True):
        """
        :type _root: TreeNode
        :type first: bool
        :rtype: bool
        """
        root = _root
        if not root:
            return first or []
        result = self.isValidBST(root.left, False) + [root.val] + self.isValidBST(root.right, False)
        return all([right > left for right, left in zip(result[1:], result)]) if first else result

```