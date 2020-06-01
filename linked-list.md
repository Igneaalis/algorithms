# Linked list

+ [Remove Nth Node From End of List](#remove-nth-node-from-end-of-list)

## Remove Nth Node From End of List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head, n):
        pastNode = nextNode = head
        for i in range(n):
            nextNode = nextNode.next
        if not nextNode:
            return head.next
        while nextNode.next:
            nextNode = nextNode.next
            pastNode = pastNode.next
        pastNode.next = pastNode.next.next
        return head

```