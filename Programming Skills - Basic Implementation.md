# Programming Skills

## Basic Implementation

### 1768. Merge Strings Alternately
https://leetcode.com/problems/merge-strings-alternately/

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:

        # bigger word
        if len(word1) > len(word2):
            big_word = word1
        else:
            big_word = word2

        # create empty string for merged 
        merged_string = []

        # iterate over the larger word, use the index to append both words

        for l in range(0,len(big_word)):
            print(l)
            if l + 1 <= len(word1):  
                merged_string.append(word1[l])   
            if l + 1 <= len(word2):  
                merged_string.append(word2[l])
            
        merged_string = ''.join(merged_string)

        return merged_string
```
faster

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:

        str_merged = ""

        if len(word1) >= len(word2):
            longest_word = word1
        else:
            longest_word = word2

        for i in range(len(longest_word)):
            if i+1 <= len(word1):
                str_merged += word1[i]
            
            if i+1 <= len(word2):
                str_merged += word2[i]
        
        return str_merged
```

### 389. Find the Difference
https://leetcode.com/problems/find-the-difference/

```python
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        
        # create dictionary
        t_dict = {}

        # add letters as keys to the dictionary
        for x in range(len(t)):
            t_dict[t[x]] = 0

        # add a count of the letters to the dictionary
        for x in range(len(t)):
            if t[x] in t_dict:
                t_dict[t[x]] += 1 

        # if the value is in s, remove 1 count from the dictionary
        for x in range(len(s)):
            if s[x] in t_dict:
                t_dict[s[x]] -= 1

        print(t_dict)

        # return the key in the dictionary where the value equals 1 as a string
        return str(list(t_dict.keys())[list(t_dict.values()).index(1)]) 
```

### 28. Find the Index of the First Occurrence in a String
https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        
        # Declare m and n as variables
        m = len(needle)
        n = len(haystack)

        # window start
        ws = 0

        # iterate window_start
        # print("end range", n - m + 1)

        for ws in range(n - m + 1):
            # print("...WS loop, window is at",ws)
            # iterate haystack
            for x in range(m):
                # print("...needle[x] loop")
                # print("index =",x,"needle[x] =",needle[x])
                if needle[x] != haystack[ws + x]:
                    # print("BREAK", needle[x], "!=", haystack[ws+x])
                    break
                if x == m - 1:
                    return ws

        return -1
```

### 242. Valid Anagram
https://leetcode.com/problems/valid-anagram/

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        
        # create dictionary of larger word
        if len(s) > len(t):
            larger_word = s
            smaller_word = t
        else:
            larger_word = t 
            smaller_word = s

        dict = {}

        # add letters as keys to the dictionary
        for x in range(len(larger_word)):
            dict[larger_word[x]] = 0

        # add a count of the letters to the dictionary
        for x in range(len(larger_word)):
            if larger_word[x] in dict:
                dict[larger_word[x]] += 1 

        # if the value is in s, remove 1 count from the dictionary
        for x in range(len(smaller_word)):
            if smaller_word[x] in dict:
                dict[smaller_word[x]] -= 1

        print(list(set(dict.values())))
    
        if list(set(dict.values())) == [0]:
            return True
        else:
            return False
```
### 283. Move Zeroes
https://leetcode.com/problems/move-zeroes/

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        for x in reversed(range(len(nums))):
            print(x)
            if nums[x] == 0:
                end = nums.pop(x)
                nums.append(end)    
        return
```

### 66. Plus One
https://leetcode.com/problems/plus-one/

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        
        # Converting integer list to string list
        s = [str(i) for i in digits]
     
        # join list items using join()
        res = int("".join(s))

        #convert to int to add 1
        res = int(res) + 1 

        #convert back to string
        res = str(res)

        #convert each letter into int again into list
        res = [int(i) for i in res]

        return res
```
