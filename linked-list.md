# Linked list

+ [Reverse linked list](#reverse-linked-list)

## Reverse linked list

https://leetcode.com/problems/reverse-linked-list/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        currentNode = head
        if currentNode and currentNode.next:
            prevNode = currentNode
            nextNode = currentNode.next
            currentNode.next = None
            currentNode = nextNode

            while currentNode.next:
                nextNode = nextNode.next
                currentNode.next = prevNode
                prevNode = currentNode
                currentNode = nextNode

            currentNode.next = prevNode
        return currentNode

```