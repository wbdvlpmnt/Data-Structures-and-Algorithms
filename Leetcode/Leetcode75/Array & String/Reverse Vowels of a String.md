# Reverse Vowels of a String

Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

 

Example 1:

Input: s = "IceCreAm"

Output: "AceCreIm"

Explanation:

The vowels in s are ['I', 'e', 'e', 'A']. On reversing the vowels, s becomes "AceCreIm".

Example 2:

Input: s = "leetcode"

Output: "leotcede"

 

Constraints:

1 <= s.length <= 3 * 105
s consist of printable ASCII characters.

```Python
class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        
        res = []
        j = 0
        vowel_arr = []
        index_arr = []

        # go through the string
        for i in s:
            # check if charecter is vowel
            if i == 'a' or i == 'e' or i =='i' or i=='o' or i=='u' or i == 'A' or i == 'E' or i =='I' or i=='O' or i=='U':
                # record the vowel
                vowel_arr.append(i)
                index_arr.append(j)
            res.append(i)
            j = j + 1

        # swap the min and max vowels 
        vowel_arr.reverse()

        for x in range(len(index_arr)):
            res[index_arr[x]] = vowel_arr[x]
        

        # return the string
        return "".join(res)
```

Approach:
- Go through the string and capture the vowels and their index (location) in the original string
- During this loop also store the string as an array (list). 
- Remember that arrays are mutable in Python, while Strings are not.
- Swap the order of the vowels with the array reverse method (python built in)
- Next go through the index array and update the result array for the indexs we stored in the index array
- Since the index array is the same size as the vowel array (which is reveresed) we can easily swap 1-1
- Finally use the join method to turn the result array back into a string