# Move Zeros

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

Example 1:

Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
Example 2:

Input: nums = [0]
Output: [0]

```Python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """

        if len(nums) == 1:
            return nums

        j = 0
        for i in range(len(nums)):
            if nums[i] != 0:
                tmp = nums[j]
                nums[j] = nums[i]
                nums[i] = tmp
                j = j + 1
        return nums
```
Approach:
- A pointer is a reference in the list
- So we have two pointers, i and j
- i iterates forward through the array 
- j refernces the last location that we swapped at
- As we encounter a non-zero we swap to the j position of the list
- We are mutating the original array, instead of creating a new one. This is called in-place.
