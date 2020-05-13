# Intervals

## Non-overlapping intervals

https://leetcode.com/problems/non-overlapping-intervals

```python
class Solution(object):
    def eraseOverlapIntervals(self, intervals):
        """
        :type intervals: List[List[int]]
        :rtype: int
        """

        intervals = sorted(intervals, key=lambda x: x[0])
        out = 0
        pstart = pend = float('-inf')
        for start, end in intervals:
            if start >= pend:
                pstart, pend = start, end
            else:
                if end <= pend:
                    pstart, pend = start, end
                out += 1
        return out

```

## Merge intervals

https://leetcode.com/problems/merge-intervals/

```python
class Solution(object):
    def merge(self, intervals):
        """
        :type intervals: List[List[int]]
        :rtype: List[List[int]]
        """

        out = []
        for i in sorted(intervals, key=lambda x: x[0]):
            # print('out: {}, i[0]: {}'.format(out, i[0]))
            if out and i[0] <= out[-1][1]:
                out[-1][1] = max(i[1], out[-1][1])
            else:
                out += [i]
        return out

```

## Insert intervals

https://leetcode.com/problems/insert-interval/

```python
class Solution(object):
    def insert(self, intervals, newInterval):
        """
        :type intervals: List[List[int]]
        :type newInterval: List[int]
        :rtype: List[List[int]]
        """

        intervals.append(newInterval)
        out = []
        for i in sorted(intervals, key=lambda x: x[0]):
            if out and i[0] <= out[-1][1]:
                out[-1][1] = max(i[1], out[-1][1])
            else:
                out += [i]
        return out

```
