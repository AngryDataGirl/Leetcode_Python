
- [Programming Skills](#programming-skills)
  - [Built-In Functions](#built-in-functions)
    - [58. Length of Last Word](#58-length-of-last-word)
    - [709. To Lower Case](#709-to-lower-case)

# Programming Skills 

## Built-In Functions

### 58. Length of Last Word
https://leetcode.com/problems/length-of-last-word/

```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        
        reversed = s[::-1]
        all_words = reversed.split()

        return len(all_words[0])
```

### 709. To Lower Case
https://leetcode.com/problems/to-lower-case/

```python
class Solution:
    def toLowerCase(self, s: str) -> str:
        return s.lower()
```
