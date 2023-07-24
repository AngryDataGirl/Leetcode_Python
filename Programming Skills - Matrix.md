# Programming Skills

## Matrix

### 1672. Richest Customer Wealth
https://leetcode.com/problems/richest-customer-wealth/

```python
class Solution:
    def maximumWealth(self, accounts: List[List[int]]) -> int:
        
        max_wealth = 0

        for x in range(len(accounts)):
            if sum(accounts[x]) > max_wealth:
                max_wealth = sum(accounts[x])

        return max_wealth
```
