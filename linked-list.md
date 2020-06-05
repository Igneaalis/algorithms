# Linked list

+ [Sort List (map() version)](#sort-list-map-version)
+ [Sort List (divide and conquer version)](#sort-list-divide-and-conquer-version)
+ [Merge Function (recursive)](#merge-function-recursive)

## Sort List (map() version)

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

        return self.mergeList(*map(self.sortList, (start, tail)))

    def mergeList(self, left, right):
        """
        :type left: ListNode
        :type right: ListNode
        :rtype: ListNode
        """
        cur = head = ListNode()
        while left and right:
            if left.val < right.val:
                cur.next = left
                left = left.next
                cur = cur.next
            else:
                cur.next = right
                right = right.next
                cur = cur.next

        while left:
            cur.next = left
            cur = cur.next
            left = left.next

        while right:
            cur.next = right
            cur = cur.next
            right = right.next

        cur.next = None

        return head.next

```

https://leetcode.com/problems/sort-list/

## Sort List (divide and conquer version)

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
        head = _head
        left, right = self.halveList(head)
        if left == right:
            return left

        left = self.sortList(left)
        right = self.sortList(right)

        return self.mergeList(left, right)

    def mergeList(self, left, right):
        """
        :type left: ListNode
        :type right: ListNode
        :rtype: ListNode
        """
        cur = head = ListNode()
        while left and right:
            if left.val < right.val:
                cur.next = left
                left = left.next
                cur = cur.next
            else:
                cur.next = right
                right = right.next
                cur = cur.next

        while left:
            cur.next = left
            cur = cur.next
            left = left.next

        while right:
            cur.next = right
            cur = cur.next
            right = right.next

        cur.next = None

        return head.next

    def halveList(self, head):
        """
        :type head: ListNode
        :rtype: (ListNode, ListNode)
        """
        fast = slow = head
        prev = None
        while fast:
            fast = fast.next
            if not fast: break

            prev = slow
            slow = slow.next
            fast = fast.next

        if prev:
            prev.next = None
        return head, slow

```

## Merge Function (recursive)

```python
def mergeList(self, left, right):
    """
    :type left: ListNode
    :type right: ListNode
    :rtype: ListNode
    """
    if left and right:
        if left.val > right.val:
            left, right = right, left
        left.next = self.mergeList(left.next, right)
    return left or right

```