# Binary tree

+ [Binary Tree Inorder Traversal](#binary-tree-inorder-traversal)

## Binary Tree Inorder Traversal

https://leetcode.com/problems/binary-tree-inorder-traversal/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        head = root
        inorderlist = []
        while head:
            if not head.left:
                inorderlist.append(head.val)
                head = head.right
            elif head.left:
                curNode = head.left
                while head.left and curNode.right and curNode.right != head:
                    curNode = curNode.right
                if not curNode.right:
                    curNode.right = head
                    head = head.left
                elif curNode.right == head:
                    inorderlist.append(head.val)
                    curNode.right = None
                    head = head.right
        return inorderlist

```