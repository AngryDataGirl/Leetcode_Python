- [1. Two Sum](#1-two-sum)
- [9. Palindrome Number](#9-palindrome-number)
- [26. Remove Duplicates from Sorted Array](#26-remove-duplicates-from-sorted-array)
- [27. Remove Element](#27-remove-element)
- [125. Valid Palindrome](#125-valid-palindrome)
- [217. Contains Duplicate](#217-contains-duplicate)
- [344. Reverse String](#344-reverse-string)
- [345. Reverse Vowels of  String](#345-reverse-vowels-of--string)
- [557. Reverse Words in a String III](#557-reverse-words-in-a-string-iii)
- [832. Flipping an Image](#832-flipping-an-image)
- [2000. Reverse Prefix of Word](#2000-reverse-prefix-of-word)
- [2108. Find First Palindromic String in the Array](#2108-find-first-palindromic-string-in-the-array)
  - [2540. Minimum Common Value](#2540-minimum-common-value)
- [905. Sort Array By Parity](#905-sort-array-by-parity)

### 1. Two Sum
https://leetcode.com/problems/two-sum/

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

### 27. Remove Element
https://leetcode.com/problems/remove-element/

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        # start both indexes at 1 
        i = j = 0

        # [0,1,2,2,3,0,4,2]
        #  i
        #  j

        for i in range(len(nums)):
            # check if previous element = current element
            if nums[i] == val:
                pass
            else:
                nums[j] = nums[i]
                j += 1
            
        return j
```

### 125. Valid Palindrome
https://leetcode.com/problems/valid-palindrome/

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        
        # "A man, a plan, a canal: Panama"
           #i 
                                      #j
        # initialize pointer
        i = 0
        j = len(s)-1

        while i < j:
            # increment i if s[i] is not a letter or number 
            while i < j and not s[i].isalnum():
                i += 1
            # control j if s[j] is not a letter or number
            while j > i and not s[j].isalnum():
                j -= 1
            # check if same
            if s[i].lower() != s[j].lower():
                return False
            # if letters are the same then need to increment i & j to continue
            i += 1
            j -= 1

        return True
```

### 217. Contains Duplicate
https://leetcode.com/problems/contains-duplicate/

regular solution

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        print(nums)
        print(set(nums))
        return len(nums) != len(set(nums))
```        

### 344. Reverse String
https://leetcode.com/problems/reverse-string/

```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        
        # ["h","e","l","l","o"]
           #i
                            #j
        # ["h","e","l","l","o"]
               #i
                        #j
        # ["h","e","l","l","o"]
                   #i
                   #j           
        
        i = 0
        j = len(s)-1

        while i < j: 
            s[i],s[j] = s[j],s[i] # have to increment at the same time otherwise you will overwrite before you can swap 
            i +=1
            j -=1         # you can also write it like this in one line i,j = i+1j-1 
```

### 345. Reverse Vowels of  String
https://leetcode.com/problems/reverse-vowels-of-a-string/
```python
class Solution:
    def reverseVowels(self, s: str) -> str:
        
        s_list = []
        for x in s:
            s_list.append(x)
        print(s_list)

        i = 0
        j = len(s_list)-1

        while i < j: 
            # print(s[i],s[j])
            while i < j and s_list[i].lower() not in ('a','e','o','i','u'):
                i += 1 
            while j > i and s_list[j].lower() not in ('a','e','o','i','u'):
                j -= 1
            s_list[i],s_list[j] = s_list[j],s_list[i] # have to increment at the same time otherwise you will overwrite before you can swap 
            i +=1
            j -=1         # you can also write it like this in one line i,j = i+1j-1 
        return "".join(s_list)
```

### 557. Reverse Words in a String III
https://leetcode.com/problems/reverse-words-in-a-string-iii/

```python
class Solution:
    def reverseWords(self, s: str) -> str:

        reconstructed = []

        words = s.split(" ")

        for word in words:
            word_as_list = []
            for letter in word:
                word_as_list.append(letter)

            i = 0
            j = len(word_as_list) -1

            while i <= j:
                # [ 1    2    3    4 ]
                # ['t', 'a', 'k', 'e']
                #   i
                #                  j

                word_as_list[i],word_as_list[j] = word_as_list[j],word_as_list[i]
                i += 1
                j -= 1

            reversed_words = ("").join(word_as_list)
            # print(reversed_words) 
            reconstructed.append(reversed_words)
            # print(reconstructed)
            x = (" ").join(reconstructed)

        return x

```

### 832. Flipping an Image
https://leetcode.com/problems/flipping-an-image/

```python
class Solution:
    def flipAndInvertImage(self, image: List[List[int]]) -> List[List[int]]:

        # it is an n x n matrix, so this is fine
        image_len = len(image) -1
        row_len = image_len
  
        # set pointers
        row = 0
        i = 0
        j = image_len

        # [[0,1,2],[0,1,2],[0,1,2]] #index
        # [[1,1,0],[1,0,1],[0,0,0]] # numbers
        #   i  
        #       j
        # [[0,1,1],[1,0,1],[0,0,0]] # result
        
        # set up while loop to loop over the rows in the image
        while row <= image_len:
            # print("outer loop",image[row])
            while i < j:
                image[row][i],image[row][j] = image[row][j],image[row][i]
                i += 1
                j -= 1
                # print("After swap",image[row])                
            # increment row 
            row += 1
            i = 0
            j = image_len

        for row in range(image_len + 1):
            for x in range(row_len + 1):
                if image[row][x] == 1:
                    image[row][x] = 0
                else:
                    image[row][x] = 1 

        return image
```

### 2000. Reverse Prefix of Word
https://leetcode.com/problems/reverse-prefix-of-word/

```python
class Solution:
    def reversePrefix(self, word: str, ch: str) -> str:
        
        # find the index of the letter, if index less than 0 there is no operation to be done so return 
        if word.find(ch) <= 0:
            return word
        
        # create list to store word
        word_to_list = []

        # make a word a list to iterate over it 
        for letter in word:
            word_to_list.append(letter)

        # create pointers 
        i = 0 
        j = word.find(ch)

        # [ 0,   1,   2,   3,  'e', 'f', 'd']
        # ['a', 'b', 'c', 'd', 'e', 'f', 'd']
        # ['d', 'b', 'c', 'a', 'e', 'f', 'd']
        #   i
        #                  j
        # ['a', 'b', 'c', 'd', 'e', 'f', 'd']
        # ['d', 'b', 'c', 'a', 'e', 'f', 'd']
        #        i
        #             j
        while i <= j:
            word_to_list[i],word_to_list[j] = word_to_list[j],word_to_list[i]
            print(word_to_list[i],word_to_list[j])
            print(i, j)
            i += 1
            j -= 1

        return ''.join(word_to_list)
```
### 2108. Find First Palindromic String in the Array
https://leetcode.com/problems/find-first-palindromic-string-in-the-array/

```python
class Solution:
    def firstPalindrome(self, words: List[str]) -> str:

        for word in words:
            # change word to list to iterate over letters
            word_as_list = []
            for letter in word:
                word_as_list.append(letter)      
            print(word_as_list)
            
            if len(word_as_list) == 1:
                return "".join(word_as_list)
                
            # now check if word is palindrome
            i = 0
            j = len(word_as_list)-1

            while i < j:
                if word_as_list[i] != word_as_list[j]:
                    print(word_as_list[i],word_as_list[j])
                    print("break")
                    break
                i += 1
                j -= 1
                if i == j or i > j:
                    print(i,j)
                    return "".join(word_as_list)
                else: 
                    pass

        return ""
```

#### 2540. Minimum Common Value
https://leetcode.com/problems/minimum-common-value/

```python
class Solution:
    def getCommon(self, nums1: List[int], nums2: List[int]) -> int:
    
        # initialize pointers
        i=j=0

        # make pointers race, nested while loop takes too long and times out
        while i < len(nums1) and j < len(nums2): 
            if nums1[i] > nums2[j]:
                j += 1
            elif nums1[i] < nums2[j]:
                i += 1
            else:
                return nums1[i]
        return -1 

```

### 905. Sort Array By Parity
https://leetcode.com/problems/sort-array-by-parity/

```python
class Solution:
    def sortArrayByParity(self, nums: List[int]) -> List[int]:
        
        # set up pointer
        i = 0
        j = len(nums)-1

        #  0  1  2  3  ## the index
        # [3, 1, 2, 4] ## the nums list 
        #  i     
        #           j     

        while i < j:
            while nums[i] % 2 == 0 and i < j:
                i += 1
            while nums[j] % 2 != 0 and j > i:
                j -= 1

            nums[i],nums[j] = nums[j],nums[i]
            i += 1
            j -= 1
            
        return nums
```