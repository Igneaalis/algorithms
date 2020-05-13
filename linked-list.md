# Linked list

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

        if head and head.next:
            prev = head
            next = head.next
            head.next = None
            head = next

            while (head.next):
                next = next.next
                head.next = prev
                prev = head
                head = next

            head.next = prev
        return head

```