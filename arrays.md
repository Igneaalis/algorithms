# Arrays

+ [Two Sum](#two-sum)
+ [Three sum (Generator version, O(n^3))](#three-sum-generator-version-on3)
+ [Three sum (Set + hash version O(n^2))](#three-sum-set--hash-version-on2)
+ [Subarray Sum Equals K](#subarray-sum-equals-k)

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

        indices = {}
        for index in range(len(nums)):
            if target - nums[index] in indices:
                return [indices[target - nums[index]], index]
            indices[nums[index]] = index

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

        for index, value in enumerate(nums):
            if index == removed:
                continue
            if target - value in nums and index != nums.index(target - value) and removed != nums.index(target - value):
                yield sorted([value, target - value])

    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """

        triplets = []
        for index, value in enumerate(nums):
            pairs = []
            for x in self.twoSum(nums, -value, index):
                if x not in pairs:
                    pairs.append(x)
            for p in pairs:
                if sorted(p + [value]) not in triplets:
                    triplets += [sorted(p + [value])]
        return triplets

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
        for index, value in enumerate(nums):
            if target - value in dict:
                removed.add((value, target - value, -target))
            dict[value] = index
        del dict

    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """

        nums.sort()
        out = set()
        for index, value in enumerate(nums):
            self.twoSum(nums[index + 1:], -value, out)
        return list(list(x) for x in out)

```

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