# Intervals

+ [Non-overlapping Intervals](#non-overlapping intervals)
+ [Merge Intervals](#merge-intervals)
+ [Insert Interval](#insert-interval)



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
        overlapped_intervals = 0
        pstart = pend = float('-inf')
        for start, end in intervals:
            if start >= pend:
                pstart, pend = start, end
            else:
                if end <= pend:
                    pstart, pend = start, end
                overlapped_intervals += 1
        return overlapped_intervals

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

        merged_intervals = []
        for interval in sorted(intervals, key=lambda x: x[0]):
            if merged_intervals and interval[0] <= merged_intervals[-1][1]:
                merged_intervals[-1][1] = max(interval[1], merged_intervals[-1][1])
            else:
                merged_intervals += [interval]
        return merged_intervals

```

## Insert interval

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
        merged_intervals = []
        for interval in sorted(intervals, key=lambda x: x[0]):
            if merged_intervals and interval[0] <= merged_intervals[-1][1]:
                merged_intervals[-1][1] = max(interval[1], merged_intervals[-1][1])
            else:
                merged_intervals += [interval]
        return merged_intervals

```
