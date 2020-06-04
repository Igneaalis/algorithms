# Linked list

+ [Sort List](#sort-list)

## Sort List

https://leetcode.com/problems/sort-list/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def sortList(self, _head):
        """
        :type _head: ListNode
        :rtype: ListNode
        """
        start = _head
        if not (start and start.next):
            return start
        prevNode, tail, head = None, start, start
        while head and head.next:
            prevNode, tail, head = tail, tail.next, head.next.next
        prevNode.next = None

        return self.mergeTwoLists(*map(self.sortList, (start, tail)))

    def mergeTwoLists(self, headA, headB):
        """
        :type headA, headB: ListNode
        :rtype: ListNode
        """
        if headA and headB:
            if headA.val > headB.val:
                headA, headB = headB, headA
            headA.next = self.mergeTwoLists(headA.next, headB)
        return headA or headB

```