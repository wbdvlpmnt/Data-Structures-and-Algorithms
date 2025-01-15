# Product of Array Except Self

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

 

Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]
Example 2:

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
 

Constraints:

2 <= nums.length <= 105
-30 <= nums[i] <= 30
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

```Python
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """

        prefix_arr = []
        postfix_arr = []
        nums_len = len(nums)
        res = []

        for i in range(nums_len):
            # calculate prefix arr (prev prefix * num[i])
            if i == 0:
                prefix_arr.append(nums[i]*1)
            else:
                prefix_arr.append(prefix_arr[i-1]*nums[i])
        
        # range(start, stop, step)
        for i in range(nums_len-1,-1, -1):
            # calculate the post fix arr
            if i == nums_len-1:
                postfix_arr.append(nums[i])
            else:
                # -1 is the last entry in the arr
                postfix_arr.append(nums[i]*postfix_arr[-1])
        
        postfix_arr.reverse()
        
        for i in range(nums_len):
            # calculate the product of arrays except self
            if i == 0:
                res.append(postfix_arr[i+1]*1)
            elif i == nums_len-1:
                res.append(prefix_arr[i-1])
            else:
                res.append(postfix_arr[i+1]*prefix_arr[i-1])
        return res
```

Approach:
-  We approach the problem with the basic 2 pass technique
- First we calculate the prefixes, this is the product of the number and previous prefixs
- Think of the prefix like the current number multiplied by all previous numbers
- Next we calculate the postfix, this time we work backwards from the end
- It is the number multipled by the product of previous numbers
- We handle the edge cases of the array by setting 1 as the default
- Then finally we calculate the product except self
- here we take the postfix i + 1 and multiply by prefix i -1
- Think of this as the the product of all previous numbers multipled by the product of all future numbers, except self

This approach is called the prefix and postfix approach, there are several other problems that use this type of approach.

