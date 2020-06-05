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
        if not (headA and headB):
            return None

        nodeA, nodeB = headA, headB
        while nodeA is not nodeB:
            nodeA = headB if not nodeA else nodeA.next
            nodeB = headA if not nodeB else nodeB.next

        return nodeA

```