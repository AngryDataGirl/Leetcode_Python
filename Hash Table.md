# Leetcode Python 

## Hash Table Questions

### 1165. Single-Row Keyboard
https://leetcode.com/problems/single-row-keyboard/

```python
class Solution:
    def calculateTime(self, keyboard: str, word: str) -> int:
        total_time = 0 
        
        key_dict = {}

        for x in range(len(keyboard)):
            key_dict[keyboard[x]] = x 
        
        print(key_dict)

        total_time = key_dict[word[0]] - total_time

        print(total_time)

        for x in range(len(word)-1):
            # print("diff", abs(key_dict[word[x+1]]-key_dict[word[x]]))
            total_time += abs(key_dict[word[x]]-key_dict[word[x+1]])

        return total_time
```
