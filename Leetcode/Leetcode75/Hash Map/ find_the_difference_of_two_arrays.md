# find_the_difference_of_two_arrays

Given two 0-indexed integer arrays nums1 and nums2, return a list answer of size 2 where:

answer[0] is a list of all distinct integers in nums1 which are not present in nums2.
answer[1] is a list of all distinct integers in nums2 which are not present in nums1.
Note that the integers in the lists may be returned in any order.

Example 1:

Input: nums1 = [1,2,3], nums2 = [2,4,6]
Output: [[1,3],[4,6]]
Explanation:
For nums1, nums1[1] = 2 is present at index 0 of nums2, whereas nums1[0] = 1 and nums1[2] = 3 are not present in nums2. Therefore, answer[0] = [1,3].
For nums2, nums2[0] = 2 is present at index 1 of nums1, whereas nums2[1] = 4 and nums2[2] = 6 are not present in nums1. Therefore, answer[1] = [4,6].
Example 2:

Input: nums1 = [1,2,3,3], nums2 = [1,1,2,2]
Output: [[3],[]]
Explanation:
For nums1, nums1[2] and nums1[3] are not present in nums2. Since nums1[2] == nums1[3], their value is only included once and answer[0] = [3].
Every integer in nums2 is present in nums1. Therefore, answer[1] = [].

Constraints:

1 <= nums1.length, nums2.length <= 1000
-1000 <= nums1[i], nums2[i] <= 1000

```Python
class Solution(object):
    def findDifference(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[List[int]]
        """
        distinct_in_one = []
        distinct_in_two = []

        nums1_dict = {}
        nums2_dict = {}

        for i in range(len(nums1)):
            nums1_dict[str(nums1[i])] = i

        for i in range(len(nums2)):
            nums2_dict[str(nums2[i])] = i

        for i in nums1_dict.keys():
            if i not in nums2_dict:
                distinct_in_one.append(int(i))

        for i in nums2_dict.keys():
            if i not in nums1_dict:
                distinct_in_two.append(int(i))

        return [distinct_in_one, distinct_in_two]
```

Approach (not optimal):

- Use dicts or objects to track uniqueness
- objects have unique keys
- can get to the objects keys or values easily and iterate
- constant time lookup
- using these properties of objects can find distinct unique numbers in eeach of the lists
