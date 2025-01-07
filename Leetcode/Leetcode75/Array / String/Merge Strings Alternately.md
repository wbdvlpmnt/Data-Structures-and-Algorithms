# Merge Strings Alternately

You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.

Example 1:

Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
Explanation: The merged string will be merged as so:
word1: a b c
word2: p q r
merged: a p b q c r
Example 2:

Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
Explanation: Notice that as word2 is longer, "rs" is appended to the end.
word1: a b
word2: p q r s
merged: a p b q r s
Example 3:

Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
Explanation: Notice that as word1 is longer, "cd" is appended to the end.
word1: a b c d
word2: p q
merged: a p b q c d

Solution:

```Python
class Solution(object):
    def mergeAlternately(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: str
        """

        char_limit = len(word1) + len(word2)
        result = ""

        i = 0
        j = 0

        for x in range(char_limit):
            if i < len(word1):
                result = result + word1[i]
                i = i + 1
            if j < len(word2):
                result = result + word2[j]
                j = j + 1

        return result
```
Approach:

We are using a two pointer approach here. i and j are our two pointers. We know that the result has to be a length equal to the sum of all charecters. We can loop through the range of all charecters, and safely access the charecter in each word using the if statements. The use of the i pointer allows us to access the charecter from word 1, and increment to get to the next charecter. Similarily, j allows us to access and increment to the next charecter in word 2. We are using string concatenation to create the result string. Finally we return the result string