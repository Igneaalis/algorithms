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

## Three sum (Generator version, O(n^3))

https://leetcode.com/problems/3sum/

```python
class Solution(object):

    def twoSum(self, nums, target, removed):
        """
        :type nums: List[int]
        :type target: int
        :type removed: int
        :rtype: List[int]
        """

        for i, v in enumerate(nums):
            if i == removed:
                continue
            if target - v in nums and i != nums.index(target - v) and removed != nums.index(target - v):
                yield sorted([v, target - v])

    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """

        out = []
        for i, v in enumerate(nums):
            pairs = []
            for x in self.twoSum(nums, -v, i):
                if x not in pairs:
                    pairs.append(x)
            for p in pairs:
                if sorted(p + [v]) not in out:
                    out += [sorted(p + [v])]
        return out

```

## Three sum (Set + hash version O(n^2))

https://leetcode.com/problems/3sum/

```python
class Solution(object):

    def twoSum(self, nums, target, removed):
        """
        :type nums: List[int]
        :type target: int
        :type removed: set
        :rtype: List[int]
        """

        dict = {}
        for i, v in enumerate(nums):
            if target - v in dict:
                removed.add((v, target - v, -target))
            dict[v] = i
        del dict

    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """

        nums.sort()
        out = set()
        for i, v in enumerate(nums):
            self.twoSum(nums[i + 1:], -v, out)
        return list(list(x) for x in out)

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