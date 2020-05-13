# Arrays

## Two sum

https://leetcode.com/problems/two-sum/

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """

        out = {}
        for i in range(len(nums)):
            if target - nums[i] in out:
                return [out[target - nums[i]], i]
            out[nums[i]] = i

```

## Three sum

https://leetcode.com/problems/3sum/

```python
class Solution(object):
    def twoSum(nums, target, removed):
        """
        :type nums: List[int]
        :type target: int
        :type removed: int
        :rtype: List[int]
        """

        out = {}
        for i in range(len(nums)):
            if i == removed:
                continue
            if target - nums[i] in out:
                return [nums[out[target - nums[i]]], nums[i]]
            out[nums[i]] = i

    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """

        out = []
        for i in range(len(nums)):
            tmp = twoSum(nums, -nums[i], i)
            if tmp:
                tmp.append(nums[i])
                tmp.sort()
                if tmp not in out:
                    out.append(tmp)
        return out

```

## Subarray sum equals k

https://leetcode.com/problems/subarray-sum-equals-k/

```python
from collections import defaultdict
from itertools import accumulate


class Solution(object):
    def subarraySum(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """

        _list, _dict, out = [0] + list(accumulate(nums)), defaultdict(int), 0
        for i in range(len(nums)):
            _dict[_list[i]] += 1
            out += _dict[_list[i + 1] - k]
        return out

```