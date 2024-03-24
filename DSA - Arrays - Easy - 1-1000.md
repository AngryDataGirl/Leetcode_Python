- [1. Two Sum](#1-two-sum)
- [121. Best Time to Buy and Sell Stock](#121-best-time-to-buy-and-sell-stock)
- [136. Single Number](#136-single-number)
- [243. Shortest Word Distance](#243-shortest-word-distance)
  - [Approach #1 (Brute-force)](#approach-1-brute-force)
  - [Approach #2 (One-pass)](#approach-2-one-pass)
  - [Why not a while loop?](#why-not-a-while-loop)
- [258. Add Digits](#258-add-digits)
- [268. Missing Number](#268-missing-number)
- [448. Find All Numbers Disappeared in an Array](#448-find-all-numbers-disappeared-in-an-array)
- [500. Keyboard Row](#500-keyboard-row)
- [771. Jewels and Stones](#771-jewels-and-stones)
- [804. Unique Morse Code Words](#804-unique-morse-code-words)
- [819. Most Common Word](#819-most-common-word)
- [867. Transpose Matrix](#867-transpose-matrix)
- [929. Unique Email Addresses](#929-unique-email-addresses)


### 1. Two Sum 
https://leetcode.com/problems/two-sum/


```python
class Solution:
  def twoSum(self, nums: List[int], target: int) -> List[int]:

    #create dictionary (which is the same as a hash table)
    table = {}

    #loop through list of numbers to store them in the dictionary, where num[i] is the number and i is the index for the number
    #you can't flip them because the same number might show up twice, and you have to go into the dict to look at value to compare
    for i in range(len(nums)):
      table[nums[i]] = i
      
    #loop through the list of numbers again
    for i in range(len(nums)):
      
      #to calculate the complement
      complement = target - nums[i]

      #check if complement in dictionary, and return the index of the complement, and index of original number
      #the AND checks to see if complement index is same as original number index bc you can't use the same number twice
      
      if complement in table and table[complement] != i:
        return [i, table[complement]]
```


### 121. Best Time to Buy and Sell Stock
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:

        # tracking min price and max profit values
        min_price = float('inf')
        max_profit = 0

        # loop through prices
        for p in range(len(prices)):
            # if the current price is smaller than min price, make that the new min price
            if prices[p] < min_price:
                min_price = prices[p]
            # otherwise, subtract min price from the current price 
            # if larger than max profit, assign it as new max profit
            elif prices[p] - min_price > max_profit:
                max_profit = prices[p] - min_price 
        
        return max_profit
```


### 136. Single Number
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

### 243. Shortest Word Distance
https://leetcode.com/problems/shortest-word-distance/

**Algorithm
- Go through the entire array looking for the first word. 
- Every time we find an occurrence of the first word, we search the entire array for the closest occurrence of the second word.
 
#### Approach #1 (Brute-force)

```python
class Solution:

    def shortestDistance(self, wordsDict: List[str], word1: str, word2: str) -> int:

        i = 0
        j = 0

        shortestDist = len(wordsDict)

        for i in range(len(wordsDict)):
            if wordsDict[i] == word1:
                for j in range(len(wordsDict)):
                    if wordsDict[j] == word2 and abs(i-j) < shortestDist:
                        shortestDist = abs(i-j)

        return shortestDist
```

#### Approach #2 (One-pass)

**Algorithm**
- you can do a single pass by checking if i is `word1` or `word2` instead of doing those in separate loops
- we set the initial value of the index to `-1` because `0` is a valid index position

```python
class Solution:

    def shortestDistance(self, wordsDict: List[str], word1: str, word2: str) -> int:

        i= 0
        i1 = -1
        i2 = -1
        shortestDist = len(wordsDict)

        for i in range(len(wordsDict)):
            if wordsDict[i] == word1:
                i1 = i
            elif wordsDict[i] == word2:
                i2 = i
                
            if i1 != -1 and i2 != -1 and abs(i1-i2) < shortestDist :
                shortestDist = abs(i1-i2)

        return shortestDist
```
#### Why not a while loop? 

it will break and stop looping when you need it to continue going through the list in case there are other occurrences of the word that are closer 


### 258. Add Digits
https://leetcode.com/problems/add-digits/

```python
class Solution:
    def addDigits(self, num: int) -> int:
        
        numsum = 0
        numlen = len(str(num))

        while numlen >= 2:
            for x in str(num):
                numsum += int(x)
  
            num = numsum
            numsum = 0
            numlen = len(str(num))

        return num
```


### 268. Missing Number
https://leetcode.com/problems/missing-number/

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        
        nums.sort()
        exp = [x for x in range(min(nums),len(nums)+1)]
        
        return sum(exp)-sum(nums)
```

### 448. Find All Numbers Disappeared in an Array
https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/

```python
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        
        actual_array = [x for x in range(1,len(nums)+1)]
        nums.sort()
        nums_set = set(nums)

        disappeared_nums = []
        for x in range(len(actual_array)):
            if actual_array[x] not in nums_set:
                disappeared_nums.append(actual_array[x])
        
        return disappeared_nums
```

### 500. Keyboard Row
https://leetcode.com/problems/keyboard-row/

```python
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        first_row = ['q','w','e','r','t','y','u','i','o','p']
        second_row = ['a','s','d','f','g','h','j','k','l']
        third_row = ['z','x','c','v','b','n','m']

        keyboard_words = []
        for word in range(len(words)):
            if set(words[word].lower()).issubset(first_row):
                keyboard_words.append(words[word])
            elif set(words[word].lower()).issubset(second_row):
                keyboard_words.append(words[word])
            elif set(words[word].lower()).issubset(third_row):
                keyboard_words.append(words[word])

        return keyboard_words
```

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
### 804. Unique Morse Code Words
https://leetcode.com/problems/unique-morse-code-words/

```python
class Solution:
    def uniqueMorseRepresentations(self, words: List[str]) -> int:
        dict = {
            "a": ".-",
            "b": "-...",
            "c": "-.-.",
            "d": "-..",
            "e": ".",
            "f": "..-.",
            "g": "--.",
            "h": "....",
            "i": "..",
            "j": ".---",
            "k": "-.-",
            "l": ".-..",
            "m": "--",
            "n": "-.",
            "o": "---",
            "p": ".--.",
            "q": "--.-",
            "r": ".-.",
            "s": "...",
            "t": "-",
            "u": "..-",
            "v": "...-",
            "w": ".--",
            "x": "-..-",
            "y": "-.--",
            "z": "--..",
        }

        morse_words = []
        for x in range(len(words)):
            word = [ ]
            for letter in words[x]:
                word.append(dict[letter])
            
            morse_words.append("".join(word))
            
        return len(set(morse_words))
```

### 819. Most Common Word
https://leetcode.com/problems/most-common-word/

```python
class Solution:
    def mostCommonWord(self, paragraph: str, banned: List[str]) -> str:
        words = {}

        symbols = "!?',;."
        for i in symbols:
            paragraph = paragraph.replace(i, " ")

        paragraph = paragraph.lower().split()

        for x in paragraph:
            if x not in words and x not in banned:
                words[x] = 0
        
        for x in paragraph:
            if x in words:
                words[x] += 1 

        return str(max(words, key=words.get))
```

### 867. Transpose Matrix
https://leetcode.com/problems/transpose-matrix/

```python
class Solution:
    def transpose(self, matrix: List[List[int]]) -> List[List[int]]:

        n_matrix = len(matrix)
        n_row = len(matrix[0])

        outer_list = []

        for i in range(n_row):
            inner_list = []    
            for j in range(n_matrix):
                inner_list.append(matrix[j][i])

            outer_list.append(inner_list)
        
        return outer_list
```

### 929. Unique Email Addresses
https://leetcode.com/problems/unique-email-addresses/

```python
class Solution:
    def numUniqueEmails(self, emails: List[str]) -> int:
         
        unique_emails_list = []

        for x in emails:
            email1 = x.split("@",1)
            domain = email1[1]
            email1 = email1[0].replace(".","")
            email2 = email1.split("+",1)[0]

            unique_email = email2+"@"+domain
            unique_emails_list.append(unique_email)

        unique_emails_dict = {}
        
        for x in unique_emails_list:
            if x not in unique_emails_dict:
                unique_emails_dict[x] = 0
        
        for x in unique_emails_list:
            if x in unique_emails_dict:
                unique_emails_dict[x] += 1 
        
        print(unique_emails_dict)
        
        return len(unique_emails_dict)
```
