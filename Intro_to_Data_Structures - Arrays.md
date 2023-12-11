- [Arrays](#arrays)
- [Accessing Elements in Arrays (read / write)](#accessing-elements-in-arrays-read--write)
- [insert](#insert)
  - [insert item into list](#insert-item-into-list)
    - [Inserting a new element at the end of the Array.](#inserting-a-new-element-at-the-end-of-the-array)
    - [Inserting a new element at the beginning of the Array.](#inserting-a-new-element-at-the-beginning-of-the-array)
    - [Inserting a new element at any given index inside the Array.](#inserting-a-new-element-at-any-given-index-inside-the-array)
  - [Writing Items into an Array with a Loop](#writing-items-into-an-array-with-a-loop)
- [search](#search)
  - [read item from list](#read-item-from-list)
  - [Reading Items from an Array with a Loop](#reading-items-from-an-array-with-a-loop)
- [delete](#delete)
- [Array Capacity \& # Array Length](#array-capacity---array-length)
- [Problem 1 : Max Consecutive Ones](#problem-1--max-consecutive-ones)
- [Problem 2 : Find Numbers with Even Number of Digits](#problem-2--find-numbers-with-even-number-of-digits)
- [Problem 3 : Squares of a Sorted Array](#problem-3--squares-of-a-sorted-array)


# Arrays

- An Array is a collection of items. 
- The items are stored in neighboring (contiguous) memory locations. 
- Because they're stored together, checking through the entire collection of items is straightforward.
- For python, we use lists

#   Accessing Elements in Arrays (read / write)

We call these numbers that identify each place indexes.

# insert 

## insert item into list

### Inserting a new element at the end of the Array.
### Inserting a new element at the beginning of the Array.
### Inserting a new element at any given index inside the Array.

## Writing Items into an Array with a Loop


# search 

## read item from list 

## Reading Items from an Array with a Loop


# delete 

# Array Capacity & # Array Length

**Length**: the number of items currently in the array 
**Capacity**: the number of items the array can hold, if full

When an Array is given as a parameter, without any additional information, you can safely assume that length == capacity. 


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