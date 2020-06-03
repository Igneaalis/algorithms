# Arrays

+ [Subarray Sum Equals K](#subarray-sum-equals-k)

## Subarray sum equals k

https://leetcode.com/problems/subarray-sum-equals-k/

```python
from collections import defaultdict


class Solution(object):
    def subarraySum(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """

        _list, _dict, sums_count = [0] + [sum(nums[:index + 1]) for index in range(len(nums))], defaultdict(int), 0
        for i in range(len(nums)):
            _dict[_list[i]] += 1
            sums_count += _dict[_list[i + 1] - k]
        return sums_count

```