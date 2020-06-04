# Binary tree

+ [Binary Search Tree Iterator](#binary-search-tree-iterator)

## Binary Search Tree Iterator

https://leetcode.com/problems/binary-search-tree-iterator/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class BSTIterator(object):

    def push(self, node):
        """
        :type node: TreeNode
        """
        while node:
            self.inorderlist.append(node)
            node = node.left

    def __init__(self, root):
        """
        :type root: TreeNode
        """
        self.root = root
        self.inorderlist = []
        self.push(root)

    def next(self):
        """
        @return the next smallest number
        :rtype: int
        """
        node = self.inorderlist.pop()
        self.push(node.right)
        return node.val

    def hasNext(self):
        """
        @return whether we have a next smallest number
        :rtype: bool
        """
        return len(self.inorderlist) != 0

# Your BSTIterator object will be instantiated and called as such:
# obj = BSTIterator(root)
# param_1 = obj.next()
# param_2 = obj.hasNext()

```