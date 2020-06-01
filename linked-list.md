# Linked list

+ [Middle of the Linked List](#middle-of-the-linked-list)

## Middle of the Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def middleNode(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        pastNode = nextNode = head
        while nextNode and nextNode.next:
            pastNode = pastNode.next
            nextNode = nextNode.next.next
        return pastNode

```