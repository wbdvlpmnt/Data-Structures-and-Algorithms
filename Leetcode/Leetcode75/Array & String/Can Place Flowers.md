# Can Place Flowers

You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots.

Given an integer array flowerbed containing 0's and 1's, where 0 means empty and 1 means not empty, and an integer n, return true if n new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule and false otherwise.

 

Example 1:

Input: flowerbed = [1,0,0,0,1], n = 1
Output: true
Example 2:

Input: flowerbed = [1,0,0,0,1], n = 2
Output: false

```Python
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """

        flowerbed_len = len(flowerbed)
        i = 0 

        # Handle the Edge Case First
        if flowerbed_len == 1 and flowerbed[0] == 0:
            return True
        elif flowerbed_len == 1 and flowerbed[0] == 1 and n == 0: 
            return True
        elif flowerbed_len == 1 and flowerbed[0] == 1 and n == 1:
            return False 

        for x in range(flowerbed_len):
            # check first edge
            if x == 0:
                if flowerbed[x] == 0 and flowerbed[x+1] == 0:
                    flowerbed[x] = 1
                    i = i + 1
            # check middle 
            if x > 0 and x < flowerbed_len - 1:
                if flowerbed[x-1] == 0 and flowerbed[x+1] == 0 and flowerbed[x] == 0:
                    flowerbed[x] = 1
                    i = i + 1
            # check last edge
            if x == flowerbed_len-1:
                if flowerbed[x-1] == 0 and flowerbed[x] == 0:
                    flowerbed[x] = 1
                    i = i + 1

        return i >= n
```

Approach:
- This problem is heavy on the edge cases so make sure to read them and handle them properly
- Next we need to do a simple scan and go through the flowerbed
- Here we need to check the first edge, middle and last edge. We use conditionals for these checks
- Next we need to check if the current plot and adjacent plots are empty if so, we increment our counter and place a plant. 
- Placing of the plant is important so that the future checks will not be thrown off.
- at the end we need to check against n because we can plant up to n number of plants, we can always have less.

