# Reverse Words in a String

Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

 

Example 1:

Input: s = "the sky is blue"
Output: "blue is sky the"
Example 2:

Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.
Example 3:

Input: s = "a good   example"
Output: "example good a"
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.
 

Constraints:

1 <= s.length <= 104
s contains English letters (upper-case and lower-case), digits, and spaces ' '.
There is at least one word in s.

```Python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """

        # Put words into an array
        res = []
        word = ""
        for i in s:
            if i != " ":
                word = word + i
            elif i == " " and len(word)>0:
                print(word)
                res.append(word)
                word=""
        
        if len(word)>0:
            res.append(word)
  
        
        # Reverse the array
        res.reverse() 

        # Join the array with single space as a string
        return " ".join(res)
```

Approach:
- Go through the word and save the words
- Ignore the spaces
- make sure to save the final word, make sure double spaces have not infilitrated the res array
- reverse the array
- join the array with a single space and return the result

