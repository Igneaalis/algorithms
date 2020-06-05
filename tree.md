# Binary tree

+ [Symmetric Tree (euler path)](#symmetric-tree-euler-path)
+ [Symmetric Tree (recursive)](#symmetric-tree-recursive)

## Symmetric Tree (euler path)

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
            if not node:
                path.append(None)
                return
            
            path.append(node.val)
            euler(node.left)
            path.append(node.val)
            euler(node.right)
            path.append(node.val)

        euler(root)
        return path == path[::-1]

```

## Symmetric Tree (recursive)

https://leetcode.com/problems/symmetric-tree/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if not root:
            return True

        def isSymmetricBst(nodeA, nodeB):
            """
            :type nodeA: TreeNode
            :type nodeB: TreeNode
            :rtype: bool
            """
            if not nodeA and not nodeB:
                return True
            elif not (nodeA and nodeB):
                return False
            else:
                return nodeA.val == nodeB.val and isSymmetricBst(nodeA.left, nodeB.right) and isSymmetricBst(
                    nodeA.right,
                    nodeB.left)

        return isSymmetricBst(root.left, root.right)

```