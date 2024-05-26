#Array #HashTable #Counting #Dictionary

# Process:
1. create a hash map and add counts of elements
2. based on some logic, return the elements that meet the criteria of counts

# 136. Single Number
https://leetcode.com/problems/single-number/

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:

        dictionary = {}
        
        # assign x to dictionary 
        for x in nums:
            if x not in dictionary:
                dictionary[x] = 0 

        # count them
        for x in nums:
            if x in dictionary:
                dictionary[x] += 1 

        keys = [k for k, v in dictionary.items() if v == 1]

        return int(keys[0])
```

# 2404. Most Frequent Even Element
[Most Frequent Even Element - LeetCode](https://leetcode.com/problems/most-frequent-even-element/description/)

```python
class Solution:

    def mostFrequentEven(self, nums: List[int]) -> int:

        numsd = {}

        for x in nums:
            if x % 2 != 0:
                pass
            else:
                if x not in numsd:
                    numsd[x] = 1
                elif x in numsd:
                    numsd[x] += 1

        if len(numsd) == 0:
            return -1

        else:    
            max_count = max(numsd.values())
            keys = [k for k, v in numsd.items() if v == max_count]

            return min(keys)
```