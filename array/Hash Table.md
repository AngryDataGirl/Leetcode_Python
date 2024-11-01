# Leetcode Python 

## Hash Table Questions

### 771. Jewels and Stones
https://leetcode.com/problems/jewels-and-stones/

```python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        
        # Create dictionairy of jewels, key = character, value = how many
        jewels_dict = {}

        for j in jewels:
            jewels_dict[j] = 0

        # For loop to iterate through stones string
        for s in stones:
            # If stone char is in jewels dict, add to value of key
            if s in jewels_dict:
                jewels_dict[s] += 1
            
        # return count of all dict values added together
        # jewels_dict.values()

        return sum(jewels_dict.values())
```

### 1512. Number of Good Pairs
https://leetcode.com/problems/number-of-good-pairs/

```python
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        
        # create list to append the pairs
        good_pairs = []

        # loop through the numbers 
        for x in range(len(nums)):
            for y in range(len(nums)):
                # this gives us the index   
                print("This is the index X",x, "index y", y)
                # this gives us the value at the index
                print("this is the value",nums[x], nums[y])
                # implement conditions to detect good pair: (i, j) is called good if nums[i] == nums[j] and i < j.
                if nums[x] == nums[y] and x < y:
                    # create tuple (so that we can add it to the good pair list as an item)
                    tuple = (x,y)
                    # append tuple to list
                    good_pairs.append(tuple)

        print(good_pairs)

        # count the length of the list
        total = len(good_pairs)

        return total
         
```

### 1165. Single-Row Keyboard
https://leetcode.com/problems/single-row-keyboard/

```python
class Solution:
    def calculateTime(self, keyboard: str, word: str) -> int:
        total_time = 0 
        
        key_dict = {}

        for x in range(len(keyboard)):
            key_dict[keyboard[x]] = x 
        
        print(key_dict)

        total_time = key_dict[word[0]] - total_time

        print(total_time)

        for x in range(len(word)-1):
            # print("diff", abs(key_dict[word[x+1]]-key_dict[word[x]]))
            total_time += abs(key_dict[word[x]]-key_dict[word[x+1]])

        return total_time
```

### 1365. How Many Numbers Are Smaller Than the Current Number
https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/

```python
class Solution:
    def smallerNumbersThanCurrent(self, nums: List[int]) -> List[int]:
        
        # sort 
        s_nums = sorted(nums)

        # create empty dictionary 
        nums_size = {}

        # add it to a dictionary if not there (index is nums smaller)
        for x in range(len(s_nums)):
            if s_nums[x] not in nums_size:
                nums_size[s_nums[x]] = x

            print(nums_size)

        final_list = []
        # for nums just get index from dict 
        for x in range(len(nums)):
            print(nums[x])
            print(nums_size[nums[x]])
            if nums[x] in nums_size:
                final_list.append(nums_size[nums[x]])
        
        return final_list
```
