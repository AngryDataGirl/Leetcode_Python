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

### 1572. Matrix Diagonal Sum
https://leetcode.com/problems/matrix-diagonal-sum/

```python
class Solution:
    def diagonalSum(self, mat: List[List[int]]) -> int:

        # create integer storing sum
        sum = 0

        # primary diagonal
        for x in range(len(mat)):
            # adds elements from first diagonal
            sum += mat[x][x]
            # adds elements from secondary diagonal
            sum += mat[len(mat) - 1 - x][x]
        # if n is odd, remove middle element since it is added twice
        if len(mat) % 2 != 0:
            sum -= mat[len(mat)//2][len(mat)//2]

        return sum
```
