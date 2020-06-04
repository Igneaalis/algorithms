# Arrays

+ [Three sum (Generator version, O(n^3))](#three-sum-generator-version-on3)
+ [Three sum (Set + hash version O(n^2))](#three-sum-set--hash-version-on2)

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
        return [list(x) for x in out]

```