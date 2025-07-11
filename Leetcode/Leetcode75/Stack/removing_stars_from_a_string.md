# removing_stars_from_a_string

You are given a string s, which contains stars \*.

In one operation, you can:

Choose a star in s.
Remove the closest non-star character to its left, as well as remove the star itself.
Return the string after all stars have been removed.

Note:

The input will be generated such that the operation is always possible.
It can be shown that the resulting string will always be unique.

Example 1:

Input: s = "leet\**cod*e"
Output: "lecoe"
Explanation: Performing the removals from left to right:

- The closest character to the 1st star is 't' in "leet\**cod*e". s becomes "lee*cod*e".
- The closest character to the 2nd star is 'e' in "lee*cod*e". s becomes "lecod\*e".
- The closest character to the 3rd star is 'd' in "lecod\*e". s becomes "lecoe".
  There are no more stars, so we return "lecoe".
  Example 2:

Input: s = "erase**\***"
Output: ""
Explanation: The entire string is removed, so we return an empty string.

Constraints:

1 <= s.length <= 105
s consists of lowercase English letters and stars \*.
The operation above can be performed on s.

```Python
class Solution(object):
    def removeStars(self, s):
        """
        :type s: str
        :rtype: str
        """

        result = []

        for i in s:
            if i == "*":
                if result:
                    result.pop()
            else:
                result.append(i)

        return ''.join(result)
```

Approach:

- Stack is a fancy word for lists where you use them with append, pop and peek list[-1]
- It is the disciplined use of list
- here the result list is our stack
- iterating through the string if we meet our condition, we interact with our stack
- the join at the end is how you go from list to string
- remember the string can be indexed like a list
