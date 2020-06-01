# Linked list

+ [Merge Two Sorted Lists](#merge-two-sorted-lists)

## Merge Two Sorted Lists

https://leetcode.com/problems/merge-two-sorted-lists/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeTwoLists(self, a, b):
        if not a or b and a.val > b.val:
            a, b = b, a
        if a:
            a.next = self.mergeTwoLists(a.next, b)
        return a

```