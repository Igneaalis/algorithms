# Arrays

+ [Two Sum](#two-sum)

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