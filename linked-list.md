# Linked list

+ [Palindrome Linked List](#palindrome-linked-list)

## Palindrome Linked List

https://leetcode.com/problems/palindrome-linked-list/

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def isPalindrome(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        mid = tail = head
        while tail and tail.next:
            mid = mid.next
            tail = tail.next.next

        if mid is None:
            return True
        if mid.next is None:
            return head.val == mid.val

        mid.next.next, mid.next, tail, mid = mid, None, mid.next.next, mid.next
        while tail:
            tail.next, mid, tail = mid, tail, tail.next

        while mid and head.val == mid.val:
            head, mid = head.next, mid.next
        return not mid

```