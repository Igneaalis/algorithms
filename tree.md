# Binary tree

+ [Validate Binary Search Tree (pythonic way)](#validate-binary-search-tree-pythonic-way)
+ [Validate Binary Search Tree (recursive)](#validate-binary-search-tree-recursive)

## Validate Binary Search Tree (pythonic way)

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

## Validate Binary Search Tree (recursive)

https://leetcode.com/problems/validate-binary-search-tree/

```python
# Definition for a binary tree root.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def check(self, root, left=None, right=None):
        """
        :type root: TreeNode
        :type left: TreeNode
        :type right: TreeNode
        :rtype: bool
        """
        if not root:
            return True
        if left is not None and root.val <= left:
            return False
        if right is not None and root.val >= right:
            return False
        return self.check(root.left, left, root.val) and self.check(root.right, root.val, right)

    def isValidBST(self, _root):
        """
        :type _root: TreeNode
        :rtype: bool
        """
        root = _root
        return self.check(root)

```