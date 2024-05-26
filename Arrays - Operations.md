
#DSA #Python #Array

### Array Operations

Types of Array operations:
- **Traversal**: Traverse through the elements of an array.
- **Insertion**: Inserting a new element in an array.
- **Deletion**: Deleting element from the array.
- **Searching**: Search for an element in the array.
- **Sorting**: Maintaining the order of elements in the array.


#Array #Array/Sorting

modifies in place 
```
nums.sort()
```

to reverse sort
```
nums.sort(reverse=True)
```



# Problem 1 : Max Consecutive Ones

Given a binary array nums, return the maximum number of consecutive 1's in the array.

1. determine starting point for the window
2. determine ending point for this window

```python

  

class Solution:

    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:

        # maintain counter for number of 1

        current_max = max_nums = 0

        for n in nums:

            # if 1, increment counter

            if n == 1:

                current_max += 1

            # encounter 0 (or not 1) use the current count of one to find max 1s until now

            elif n != 1:

                max_nums = max(max_nums, current_max)

                # reset counter

                current_max = 0

  

        # return max in the end

        return max(max_nums, current_max)

```

  

# Problem 2 : Find Numbers with Even Number of Digits

Given an array nums of integers, return how many of them contain an even number of digits.

  

```python

class Solution:

    def findNumbers(self, nums: List[int]) -> int:

        # counter for total even

        total_even = 0

        for x in nums:

            # if length of the digit (converted to str to count) modulo 2 is 0, then it is even

            if len(str(x))%2 == 0:

                # add to counter

                total_even += 1

            else:

                pass

        return total_even

```

  

# Problem 3 : Squares of a Sorted Array

Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

  

```python

class Solution:

    def sortedSquares(self, nums: List[int]) -> List[int]:

        squared_list = []

        for x in nums:

            squared_list.append(x*x)

        squared_list.sort()

        return squared_list

```