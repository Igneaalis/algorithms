# Intervals

+ [Non-overlapping Intervals](#non-overlapping-intervals)
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

        intervals_count = len(intervals)
        if intervals_count  <= 1:
            return 0
        rightsorted_intervals = sorted(intervals, key=lambda x: x[1])
        counter = 0
        last_end = float("-inf")
        for interval in rightsorted_intervals:
            if interval[0] >= last_end:
                last_end = interval[1]
                counter += 1
        return intervals_count - counter

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
