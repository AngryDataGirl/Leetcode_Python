
### 1221. Split a String in Balanced Strings
https://leetcode.com/problems/split-a-string-in-balanced-strings/

```python
class Solution:
    def balancedStringSplit(self, s: str) -> int:

        balance = 0
        counter = 0
        
        for x in s:
            if x == 'L':
                balance += 1 
            elif x == 'R':
                balance -= 1
            
            if balance == 0:
                counter += 1  
        
        return counter
```

### 1323. Maximum 69 Number
https://leetcode.com/problems/maximum-69-number/

```python
class Solution:
    def maximum69Number (self, num: int) -> int:
        
        numl = [int(str(num)[x]) for x in range(len(str(num)))]

        for x in range(len(numl)):
            if numl[x] == 9:
                pass
            elif numl[x] == 6:
                numl[x] = 9
                break

        nums = [str(numl[x]) for x in range(len(numl))]
        nums = int("".join(nums))
        print(nums, num)

        return max(nums,num)
```