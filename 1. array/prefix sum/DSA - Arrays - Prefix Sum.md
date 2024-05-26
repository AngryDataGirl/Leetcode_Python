- [1480. Running Sum of 1d Array](#1480-running-sum-of-1d-array)

### 1480. Running Sum of 1d Array
https://leetcode.com/problems/running-sum-of-1d-array//

```Python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        prefix = [nums[0]]
        for i in range(1, len(nums)):
            prefix.append(prefix[-1] + nums[i])
        return prefix
```
