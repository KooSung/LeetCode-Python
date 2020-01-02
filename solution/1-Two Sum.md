### Description:  
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
```python
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

### Solution: 
#### 1. 
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        if nums is None:
            return None
        for i, num in enumerate(nums):
            if target - num in nums[i+1:]:
                ind = nums[i+1:].index(target - num)
                return [i, i+1+ind]
```

#### 2.
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        if len(nums) == 0:
            return None
        hashdict = {} # {value:index}
        for i, num in enumerate(nums):
            hashdict[num] = i
        for j, num in enumerate(nums):
            res = hashdict.get(target -num)
            if res is not None and j != res:
                return [j, res]
```           