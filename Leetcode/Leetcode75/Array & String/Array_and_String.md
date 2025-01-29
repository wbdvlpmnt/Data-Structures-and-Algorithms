# Array and String Summary

## Key Points

- **Edge Cases**: Always consider edge cases. Read the problem statement carefully to understand all constraints and special cases.
- **Problem Understanding**: Ensure you fully understand the problem before jumping into coding. Sometimes the solution is simpler than it initially appears.

## Python Tips

- **Length Calculation**: The `len` function in Python calculates the length of a list or string. It starts counting from 1.
- **Integer Division**: The double division (`//`) in Python performs integer division, meaning it divides and then rounds down to the nearest whole number (truncates the decimal).
- **Positive Infinity**: `float('inf')` represents positive infinity in Python.
- **Appending to a List**: Use the `append` method to add elements to a list.

## Iterating Through Arrays

There are several ways to iterate through arrays in Python:

1. **Using `range` and `len`**:

   ```Python
   for y in range(len(candies)):
       if candies[y] + extraCandies >= max(candies):
           # Your logic here
   ```

2. **Direct Iteration**:

   ```Python
   for i in gems:
       # Your logic here
   ```

3. **Using `enumerate`**:

   ```Python
   gems = [10, 20, 30]
   for index, value in enumerate(gems):
       # Your logic here
   ```

4. **While Loop**:

   ```Python
   i = 0
   while i < len(gems):
       # Your logic here
       i += 1
   ```

5. **Iterating Backwards**:
   ```Python
   for i in range(len(gems)-1, -1, -1):
       # Your logic here
   ```

## String and List Conversion

- **Convert String to List**: You can iterate through a string and convert it to a list.
- **Convert List to String**: Use the `join` method to convert a list back into a string.
  ```Python
  res = ['h', 'i']
  result_string = "".join(res)  # Output: "hi"
  ```

## Additional Tips

- **Sublist Creation**: `[:i]` creates a sublist from the start of the list up to (but not including) index `i`.
- **Using Pointers**: When you need to check other elements of the list as you iterate through it, consider using pointers. For example, `i` can be incremented and used to check adjacent or previous elements.
- **Handling Large Numbers**: Be mindful of integer overflow and large number calculations. Python handles large integers well, but it's good practice to be aware of potential performance issues.

## Practice Problems

- **Kids With the Greatest Number of Candies**:

  ```Python
  for y in range(len(candies)):
      if candies[y] + extraCandies >= max(candies):
          res.append(True)
      else:
          res.append(False)
  ```

- **Reverse Vowels of a String**:

  ```Python
  vowels = "aeiouAEIOU"
  s = list(s)
  i, j = 0, len(s) - 1
  while i < j:
      if s[i] in vowels and s[j] in vowels:
          s[i], s[j] = s[j], s[i]
          i += 1
          j -= 1
      if s[i] not in vowels:
          i += 1
      if s[j] not in vowels:
          j -= 1
  return "".join(s)
  ```

- **Merge Strings Alternately**:

  ```Python
  result = []
  for i in range(max(len(word1), len(word2))):
      if i < len(word1):
          result.append(word1[i])
      if i < len(word2):
          result.append(word2[i])
  return "".join(result)
  ```

- **Reverse Words in a String**:

  ```Python
  words = s.split()
  words.reverse()
  return " ".join(words)
  ```

- **Product of Array Except Self**:
  ```Python
  length = len(nums)
  answer = [0]*length
  answer[0] = 1
  for i in range(1, length):
      answer[i] = nums[i - 1] * answer[i - 1]
  R = 1
  for i in reversed(range(length)):
      answer[i] = answer[i] * R
      R *= nums[i]
  return answer
  ```

## Conclusion

Understanding and mastering these fundamental concepts and techniques will significantly enhance your problem-solving skills in algorithms and data structures. Practice regularly and review these notes to reinforce your knowledge.
