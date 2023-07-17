# Programming Skills 

## Math

### 860. Lemonade Change
https://leetcode.com/problems/lemonade-change/

```python
class Solution:
    def lemonadeChange(self, bills: List[int]) -> bool:

        change = {5: 0, 10: 0, 20: 0}

        for x in range(len(bills)):
            if bills[x] in change:
                change[bills[x]] += 1
            
            if bills[x] > 5:
                # print(bills[x])
                # print(change)
                if bills[x] == 10 and change[5] > 0:
                    change[5] -= 1
                elif bills[x] == 20 and change[10] > 0 and change[5] > 0:
                    change[10] -= 1
                    change[5] -= 1
                elif bills[x] == 20 and change[5] >= 3:
                    change[5] -= 3 
                else:
                    return False

        return True
```
