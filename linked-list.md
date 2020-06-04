# Linked list

+ [Reorder List (deque)](#reorder-list-deque)

## Reorder List (deque)

https://leetcode.com/problems/reorder-list/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reorderList(self, head):
        prev, curr = ListNode(0), head
        q = collections.deque()
        while head:
            q.append(head)
            head = head.next

        i = 1
        while q:
            if i & 1:
                curr = q.popleft()
            else:
                curr = q.pop()
            prev.next = curr
            prev = curr
            i += 1
        if curr: curr.next = None

```