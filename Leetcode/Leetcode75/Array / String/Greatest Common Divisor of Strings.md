# Greatest Common Divisor of Strings

For two strings s and t, we say "t divides s" if and only if s = t + t + t + ... + t + t (i.e., t is concatenated with itself one or more times).

Given two strings str1 and str2, return the largest string x such that x divides both str1 and str2.

Example 1:

Input: str1 = "ABCABC", str2 = "ABC"
Output: "ABC"
Example 2:

Input: str1 = "ABABAB", str2 = "ABAB"
Output: "AB"
Example 3:

Input: str1 = "LEET", str2 = "CODE"
Output: ""

Solution:

```Python
class Solution:
    def gcdOfStrings(self, str1, str2):
        # Determine the shorter string as the potential divisor
        shorter = str1 if len(str1) < len(str2) else str2

        # Iterate over all prefixes of the shorter string
        for i in range(len(shorter), 0, -1):
            candidate = shorter[:i]

            # Check if candidate divides both str1 and str2
            if len(str1) % len(candidate) == 0 and len(str2) % len(candidate) == 0:
                if str1 == candidate * (len(str1) // len(candidate)) and str2 == candidate * (len(str2) // len(candidate)):
                    return candidate

        return ""
```

Approach:
Iterate Over Possible Prefixes:

- Start with the entire shorter string and reduce its length step by step (longest prefix first).
  Check Divisibility:
- Check if the length of both str1 and str2 is divisible by the current prefix length.
- Use the prefix to reconstruct str1 and str2 by repeating it the required number of times.
  Return the Valid Prefix:
- If a valid prefix is found, return it immediately.
- If no prefix works, return an empty string ("").
