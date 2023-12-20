- [1. Two Sum](#1-two-sum)
- [9. Palindrome Number](#9-palindrome-number)
- [26. Remove Duplicates from Sorted Array](#26-remove-duplicates-from-sorted-array)

### 1. Two Sum

The other method (not two - pointer), more space since you create a dictionary 
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        table = {}

        for i in range(len(nums)):
            table[nums[i]] = i

        print(table)

        for i in range(len(nums)):
            complement = target - nums[i]
            if complement in table and table[complement] != i:
                return [i, table[complement]]
```
two pointer method

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        #[2,7,11,15]
        #   i
        #         j 

        # initialize pointers
        i = 0
        j = len(nums)-1

        # loop through nums
        while i < len(nums): 

            # if j & i are at the same index, skip to next iteration by incrementing i and resetting j to last item
            if j == i:
                i += 1
                j = len(nums)-1
            else:
                pass
            
            # if it doesnt find the solution, move j to the left
            if target - nums[i] != nums[j]:
                j -= 1
            # if it finds solution, return indices
            elif target - nums[i] == nums[j]:
                return [i,j]
            else:
                pass

```

### 9. Palindrome Number
https://leetcode.com/problems/palindrome-number/

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:

        x = str(x)
        j = len(x)-1

        for i in range(len(x)):
            # when the pointers in same spot 
            # >= because even numbers have no middle
            # pointer will skip each other
            if i >= j: 
                return True
            elif x[i] == x[j]:
                j -= 1
            else:
                return False

#examples:
        #index   012
        #x       121
        #         i
        #         j

        # 01
        # 11
        # i
        #  j

        # 0123
        # 4444
        #   i
        #  j
```

### 26. Remove Duplicates from Sorted Array
https://leetcode.com/problems/remove-duplicates-from-sorted-array/

```python

class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        #The first index updates the value in our input array while reading the data from the second index

        #First Index is responsible for writing unique values in our input array, while Second Index will read the input array and pass all the distinct elements to First Index.

        # start both indexes at 1 
        i = j = 1

        # [0,0,1,1,1,2,2,3,3,4]
        #      i
        #       j

        for i in range(1,len(nums)):
            # check if previous element = current element
            if nums[i] == nums[i-1]:
                pass
            else:
                nums[j] = nums[i]
                j += 1
            
        return j
        ```