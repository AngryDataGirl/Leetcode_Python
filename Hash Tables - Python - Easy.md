### 771. Jewels and Stones
https://leetcode.com/problems/jewels-and-stones/

```python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        
        # Create dictionairy of jewels, key = character, value = how many
        jewels_dict = {}

        for j in jewels:
            jewels_dict[j] = 0

        # For loop to iterate through stones string
        for s in stones:
            # If stone char is in jewels dict, add to value of key
            if s in jewels_dict:
                jewels_dict[s] += 1
            
        # return count of all dict values added together
        # jewels_dict.values()

        return sum(jewels_dict.values())
```
