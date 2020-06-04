# Linked list

+ [Linked List Cycle II](#linked-list-cycle-ii)

## Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def detectCycle(self, _head):
        tail = curNode = head = _head
        while curNode and curNode.next:
            tail = tail.next
            curNode = curNode.next.next
            if tail is curNode:
                break
        else:
            return None
        while head is not tail:
            tail = tail.next
            head = head.next
        return head

```