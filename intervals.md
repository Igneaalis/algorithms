# Intervals

## Non-overlapping intervals

```python
class Solution(object):
    @staticmethod
    def eraseOverlapIntervals(intervals):
        """
        :type intervals: List[List[int]]
        :rtype: int
        """

        print(intervals)
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


print(Solution.eraseOverlapIntervals([[1, 2], [2, 3], [3, 4], [1, 3]]), '\n')  # [[1, 2], [2, 3], [3, 4], [1, 3]] \n1

print(Solution.eraseOverlapIntervals([[1, 2], [1, 2], [1, 2]]), '\n')  # [[1, 2], [1, 2], [1, 2]] \n2

print(Solution.eraseOverlapIntervals([[1, 2], [2, 3]]))  # [[1, 2], [2, 3]] \n0

```

## Insert intervals

```python
class Solution(object):
    @staticmethod
    def insert(intervals, newInterval):
        """
        :type intervals: List[List[int]]
        :type newInterval: List[int]
        :rtype: List[List[int]]
        """

        print(intervals, newInterval)
        intervals.append(newInterval)
        out = []
        for i in sorted(intervals, key=lambda x: x[0]):
            if out and i[0] <= out[-1][1]:
                out[-1][1] = max(i[1], out[-1][1])
            else:
                out += [i]
        return out


print(Solution.insert([[1, 3], [6, 9]], [2, 5]), '\n')  # [[1, 3], [6, 9]] [2, 5] \n[[1, 5], [6, 9]]

print(Solution.insert([[1, 2], [3, 5], [6, 7], [8, 10], [12, 16]],
                      [4, 8]))  # [[1, 2], [3, 5], [6, 7], [8, 10], [12, 16]] [4, 8] \n[[1, 2], [3, 10], [12, 16]]

```

## Merge intervals

```python
class Solution(object):
    @staticmethod
    def merge(intervals):
        """
        :type intervals: List[List[int]]
        :rtype: List[List[int]]
        """

        print(intervals)
        out = []
        for i in sorted(intervals, key=lambda x: x[0]):
            # print('out: {}, i[0]: {}'.format(out, i[0]))
            if out and i[0] <= out[-1][1]:
                out[-1][1] = max(i[1], out[-1][1])
            else:
                out += [i]
        return out


print(Solution.merge([[1, 3], [2, 6], [8, 10], [15, 18]]),
      '\n')  # [[1, 3], [2, 6], [8, 10], [15, 18]] \n[[1, 6], [8, 10], [15, 18]]

print(Solution.merge([[1, 4], [4, 5]]))  # [[1, 4], [4, 5]] \n[[1, 5]]

```