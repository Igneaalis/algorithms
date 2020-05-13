# Arrays

## Two sum

https://leetcode.com/problems/two-sum/

```python
class Solution(object):
    @staticmethod
    def twoSum(nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """

        print(nums, target)
        out = {}
        for i in range(len(nums)):
            if target - nums[i] in out:
                return [out[target - nums[i]], i]
            out[nums[i]] = i


print(Solution.twoSum([2, 7, 11, 15], 9))  # [2, 7, 11, 15] 9 \n[0, 1]

```

## Three sum

https://leetcode.com/problems/3sum/

```python
class Solution(object):
    @staticmethod
    def threeSum(nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """

        print(nums)
        out = []
        for i in range(len(nums)):
            tmp = Solution.twoSum(nums, -nums[i], i)
            if tmp:
                tmp.append(nums[i])
                tmp.sort()
                if tmp not in out:
                    out.append(tmp)
        return out

    @staticmethod
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


print(Solution.threeSum([-1, 0, 1, 2, -1, -4]))  # [-1, 0, 1, 2, -1, -4] \n[[-1, 0, 1], [-1, -1, 2]]

```

## Subarray sum equals k

https://leetcode.com/problems/subarray-sum-equals-k/

```python
from collections import defaultdict
from itertools import accumulate


class Solution(object):
    @staticmethod
    def subarraySum(nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """

        print(nums)
        _list, _dict, out = [0] + list(accumulate(nums)), defaultdict(int), 0
        for i in range(len(nums)):
            _dict[_list[i]] += 1
            out += _dict[_list[i + 1] - k]
        return out


print(Solution.subarraySum([1, 1, 1], 2))  # [1, 1, 1] \n2

```