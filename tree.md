# Binary tree

+ [Binary Tree Inorder Traversal (iterative, threaded)](#binary-tree-inorder-traversal-iterative-threaded)
+ [Binary Tree Inorder Traversal (recursive)](#binary-tree-inorder-traversal-recursive)
+ [Binary Tree Inorder Traversal (iterative, stack)](#binary-tree-inorder-traversal-iterative-stack)

## Binary Tree Inorder Traversal (iterative, threaded)

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

## Binary Tree Inorder Traversal (recursive)

https://leetcode.com/problems/binary-tree-inorder-traversal/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    inorderlist = []

    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        head = root
        return self.inorderTraversal(head.left) + [head.val] + self.inorderTraversal(head.right) if head else []

```

## Binary Tree Inorder Traversal (iterative, stack)

https://leetcode.com/problems/binary-tree-inorder-traversal/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    inorderlist = []

    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root:
            return []
        stack = []
        inorderlist = []
        while stack or root:
            if root:
                stack.append(root)
                root = root.left
            else:
                node = stack.pop()
                inorderlist.append(node.val)
                root = node.right
        return inorderlist

```