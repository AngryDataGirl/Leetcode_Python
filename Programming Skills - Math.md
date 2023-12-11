- [Programming Skills](#programming-skills)
  - [Math](#math)
    - [1491. Average Salary Excluding the Minimum and Maximum Salary](#1491-average-salary-excluding-the-minimum-and-maximum-salary)
    - [860. Lemonade Change](#860-lemonade-change)


# Programming Skills 

## Math

### 1491. Average Salary Excluding the Minimum and Maximum Salary
https://leetcode.com/problems/average-salary-excluding-the-minimum-and-maximum-salary/

```python
class Solution:
    def average(self, salary: List[int]) -> float:

        salary.remove(min(salary))
        salary.remove(max(salary))

        # print(min_sal, max_sal)
        return sum(salary)/len(salary)
```

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
