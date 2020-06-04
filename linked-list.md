# Linked list

+ [Intersection of Two Linked Lists](#intersection-of-two-linked-lists)

## Intersection of Two Linked Lists

https://leetcode.com/problems/intersection-of-two-linked-lists/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def getIntersectionNode(self, _headA, _headB):
        """
        :type _headA, _headB: ListNode
        :rtype: ListNode
        """
        headA, headB = _headA, _headB
        if not headA or not headB:
            return None
        curA, curB = headA, headB
        flagA, flagB = False, False
        while curA is not curB:
            if not flagA and not curA.next:
                flagA = True
                curA = headB
            else:
                curA = curA.next
            if not flagB and not curB.next:
                flagB = True
                curB = headA
            else:
                curB = curB.next
        return curA

```