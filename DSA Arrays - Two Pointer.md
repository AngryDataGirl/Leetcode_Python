- [1. Two Sum](#1-two-sum)
- [9. Palindrome Number](#9-palindrome-number)
- [26. Remove Duplicates from Sorted Array](#26-remove-duplicates-from-sorted-array)
- [27. Remove Element](#27-remove-element)
- [125. Valid Palindrome](#125-valid-palindrome)
- [217. Contains Duplicate](#217-contains-duplicate)
- [246. Strobogrammatic Number](#246-strobogrammatic-number)
- [344. Reverse String](#344-reverse-string)
- [345. Reverse Vowels of  String](#345-reverse-vowels-of--string)
- [349. Intersection of Two Arrays](#349-intersection-of-two-arrays)
- [392. Is Subsequence](#392-is-subsequence)
- [445. Assign Cookies](#445-assign-cookies)
- [557. Reverse Words in a String III](#557-reverse-words-in-a-string-iii)
- [832. Flipping an Image](#832-flipping-an-image)
- [905. Sort Array By Parity](#905-sort-array-by-parity)
- [1089. Duplicate Zeros](#1089-duplicate-zeros)
- [1099. Two Sum Less Than K](#1099-two-sum-less-than-k)
- [1470. Shuffle the Array](#1470-shuffle-the-array)
- [1528. Shuffle String](#1528-shuffle-string)
- [1662. Check If Two String Arrays are Equivalent](#1662-check-if-two-string-arrays-are-equivalent)
- [2000. Reverse Prefix of Word](#2000-reverse-prefix-of-word)
- [2006. Count Number of Pairs With Absolute Difference K](#2006-count-number-of-pairs-with-absolute-difference-k)
- [2108. Find First Palindromic String in the Array](#2108-find-first-palindromic-string-in-the-array)
  - [2441. 2441. Largest Positive Integer That Exists With Its Negative](#2441-2441-largest-positive-integer-that-exists-with-its-negative)
  - [2540. Minimum Common Value](#2540-minimum-common-value)
- [2562. Find the Array Concatenation Value](#2562-find-the-array-concatenation-value)
- [2824. Count Pairs Whose Sum is Less than Target](#2824-count-pairs-whose-sum-is-less-than-target)
- [2942. Find Words Containing Character](#2942-find-words-containing-character)

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

### 246. Strobogrammatic Number
https://leetcode.com/problems/strobogrammatic-number/

```python
class Solution:
    def isStrobogrammatic(self, num: str) -> bool:
        
        # use palindrome logic since it would have to be symmetrical --- (0,1,8) or (6 and 9)
        i = 0
        j = len(num) -1

        while i <= j:
            if (num[i] == '6' and num[j] != '9') or (num[i] != '6' and num[j] == '9') or (num[i] == '9' and num[j] != '6') or (num[i] != '9' and num[j] == '6'):
                return False
            if num[i] in ('0','1','8') and num[i] != num[j]:
                return False
            if num[i] not in ('0','1','6','8','9'):
                return False
            else:
                pass

            i += 1 
            j -= 1

        return True
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

### 349. Intersection of Two Arrays

non-pointer solution
```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        
        # find longer array
        if len(nums1) > len(nums2):
            longer_nums = nums1
            shorter_nums = nums2
        else:
            longer_nums = nums2
            shorter_nums = nums1

        intersection = []

        for x in longer_nums:
            if x in shorter_nums:
                intersection.append(x)

        return set(intersection)
```
built-in set intersection
```python
class Solution:
    def intersection(self, nums1, nums2):
        set1 = set(nums1)
        set2 = set(nums2)
        return list(set2 & set1)
```

2-pointer solutiuon
```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        
        # find shorter array
        if len(nums1) > len(nums2):
            long, short = nums1, nums2
        else:
            long, short = nums2, nums1
            
        i = j = 0 

        intersection = []
    
        while i <= len(short)-1:
            while j <= len(long)-1:
                if short[i] == long[j] and short[i] not in intersection:
                    intersection.append(short[i])
                j += 1 
            i += 1
            j = 0
        
        return intersection
```

### 392. Is Subsequence
https://leetcode.com/problems/is-subsequence/

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        
        i = 0
        j = 0

        # s is always the subsequence 
        
        # a b c
        #     j
        
        # a h b g d c
        #           i 

        # ????????
        if len(s) == 0:
            return True

        while i <= len(t) - 1:
            print(t[i])
            if t[i] == s[j]:
                j += 1
            
            if j > len(s) -1:
                return True

            i += 1

        return False

```

### 445. Assign Cookies
- you cannot increment a counter for an outer loop within the inner loop without a bunch of additional if/then statements
- combining it is easier

```python
class Solution:
    def findContentChildren(self, g: List[int], s: List[int]) -> int:
        
        g.sort()
        s.sort()
        kids = g
        cookies = s

        k = c = 0

        # loops
        while k < len(kids) and c < len(cookies):
            if cookies[c] >= kids[k]:
                k += 1 
                c += 1 
            else:
                c += 1 
        
        return k
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

### 1089. Duplicate Zeros
https://leetcode.com/problems/duplicate-zeros/

```python
class Solution:
    def duplicateZeros(self, arr: List[int]) -> None:
        """
        Do not return anything, modify arr in-place instead.
        """
        
        i = 0 
        j = len(arr)-1 # start j from the end bc going forward you would be overwriting elements

        # [1,0,2,3,0,4,5,0]
        #    i
        #                j
        
        while i < len(arr)-1:
            if arr[i] ==0:
                while j > i:
                    arr[j] = arr[j-1]
                    j -= 1
                i += 2 # skip over the duplicated 0
                j = len(arr)-1 # reset j
            else:
                i += 1
        
        return arr
```

### 1099. Two Sum Less Than K
https://leetcode.com/problems/two-sum-less-than-k/

```python
class Solution:
    def twoSumLessThanK(self, nums: List[int], k: int) -> int:
        
        nums.sort()

        i = 0 
        j = len(nums) - 1
        max_sum = -1 

        # [1, 8, 23, 24, 33, 34, 54, 75]
        #     i               
        #                             j


        while i < j:
            sum = nums[i] + nums[j]
            if sum < k:
                max_sum = max(max_sum,sum)
                i += 1 
            else:
                j -= 1 

        return max_sum
```

### 1470. Shuffle the Array
https://leetcode.com/problems/shuffle-the-array/

```python
class Solution:
    def shuffle(self, nums: List[int], n: int) -> List[int]:

        final_array = []

        i = 0
        j = n

        print(i,j)
        # [0,1,2,3,4,5]
        # [2,5,1,3,4,7]
        #  i 
        #        j
        
        while i < n:
            final_array.append(nums[i])
            final_array.append(nums[j])
            
            j += 1 
            i += 1 

        return final_array
```

### 1528. Shuffle String
https://leetcode.com/problems/shuffle-string/

```python
class Solution:
    def restoreString(self, s: str, indices: List[int]) -> str:

        # [0,1,2,3,4,5,6,7] # SHUFFLED STRING i will assign letter to right place
        #    i 


        # [4,5,6,7,0,2,1,3] # INDICES we need to use index to get letter
        #  j
        # [c,o,d,e,l,e,e,t] # S
        #          j

        i = j = 0

        if len(s) == 1:
            return s

        shuffled_string = [x for x in range(len(indices))]

        while i < len(indices)-1:
            while j < len(s)-1:
                if i != indices[j]:
                    pass
                    j += 1 
                if i == indices[j]:
                    shuffled_string[i] = s[j]
                    i += 1
                    j = 0
            i += 1 
        
        print(shuffled_string)
        return "".join(shuffled_string)

```

### 1662. Check If Two String Arrays are Equivalent
https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/

```python
class Solution:
    def arrayStringsAreEqual(self, word1: List[str], word2: List[str]) -> bool:

        # concatenate so we can loop through the entire thing             
        word1 = "".join(word1)
        word2 = "".join(word2)
        print(word1, word2) 


        # check that words are same length
        if len(word1) == len(word2):

            # set up pointer
            i = j = 0

            # need index to iterate through list AND string
            for x in range(len(word1)):
                if word1[x] != word2[x]:
                    return False
            
            return True

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

### 2006. Count Number of Pairs With Absolute Difference K
https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/

```python
class Solution:
    def countKDifference(self, nums: List[int], k: int) -> int:

        i = 0
        j = i + 1 

        pairs = 0 

        while i < len(nums):
            while j < len(nums):
                if abs(nums[i] - nums[j]) == k:
                    pairs += 1 
                j += 1
            i += 1
            j = i + 1 
          
        return pairs
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

#### 2441. 2441. Largest Positive Integer That Exists With Its Negative
https://leetcode.com/problems/largest-positive-integer-that-exists-with-its-negative/

```python
class Solution:
    def findMaxK(self, nums: List[int]) -> int:
        
        i = 0
        j = len(nums)-1
        largest_int = 0

        # [-1,10,6,7,-7,1]
        #          i           
        #             j
        
        while i < j:
            while nums[i] + nums[j] != 0 and j > i:
                j -= 1
            if nums[i] + nums[j] == 0 and i != j and abs(nums[j]) > largest_int:
                largest_int = abs(nums[j])
                        
            j = len(nums)-1
            i += 1
        
        if largest_int == 0:
            return -1 
        else:
            return largest_int
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

### 2562. Find the Array Concatenation Value
https://leetcode.com/problems/find-the-array-concatenation-value/

```python
class Solution:
    def findTheArrayConcVal(self, nums: List[int]) -> int:
        
        i = 0 
        j = len(nums) -1 

        concat_total = 0

        while i < len(nums) and j >= i:
            if j > i:
                concat_val = str(nums[i])+str(nums[j])
                concat_total = concat_total + int(concat_val)
            elif j == i:
                concat_total = concat_total + nums[i]

            j -= 1
            i += 1 
        
        return concat_total
```


### 2824. Count Pairs Whose Sum is Less than Target
https://leetcode.com/problems/count-pairs-whose-sum-is-less-than-target/

```python
class Solution:
    def countPairs(self, nums: List[int], target: int) -> int:
        
        i = 0
        j = i + 1 

        count = 0

        while i < len(nums):

            while j < len(nums):
                # print("i",nums[i],"j",nums[j])
                # print(count)
                if nums[i] + nums[j] < target:
                    count += 1 

                j += 1 

            i += 1
            j = i + 1

        return count
```

### 2942. Find Words Containing Character
https://leetcode.com/problems/find-words-containing-character/ 

```python
class Solution:
    def findWordsContaining(self, words: List[str], x: str) -> List[int]:
        
        final_array = []

        for index in range(len(words)):
            for letter in words[index]:
                if x == letter:
                    final_array.append(index)
                    break

        return final_array
```
