# Increasing Triplet Subsequence

Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exists, return false.

Example 1:

Input: nums = [1,2,3,4,5]
Output: true
Explanation: Any triplet where i < j < k is valid.
Example 2:

Input: nums = [5,4,3,2,1]
Output: false
Explanation: No triplet exists.
Example 3:

Input: nums = [2,1,5,0,4,6]
Output: true
Explanation: The triplet (3, 4, 5) is valid because nums[3] == 0 < nums[4] == 4 < nums[5] == 6.

Constraints:

1 <= nums.length <= 5 \* 105
-231 <= nums[i] <= 231 - 1

```Python
class Solution(object):
    def increasingTriplet(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """

        first = second = float('inf')
        for n in nums:
            if n <= first:
                first = n
            elif n <= second:
                second = n
            else:
                return True
        return False
```

Approach:
The loop iterates through the list nums and uses the following rules:

If n <= first:
Update first to the current number n.
This ensures first always holds the smallest number encountered so far.

Example:

For nums = [5, 4, 3], first keeps getting updated because all numbers are smaller than or equal to the current first.
Else If n <= second:
Update second to the current number n.
This ensures second holds the smallest number encountered after first.

Example:

For nums = [1, 2, 0], first = 1, then second = 2. When n = 0, first is updated to 0, but second remains 2.
Else:
If n is greater than both first and second, it means we have found an increasing triplet (first < second < n), so the function returns True.

Example:

For nums = [1, 2, 3], first = 1, second = 2, and when n = 3, we return True.
