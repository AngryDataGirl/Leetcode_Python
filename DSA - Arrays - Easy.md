- [1. Two Sum](#1-two-sum)
- [121. Best Time to Buy and Sell Stock](#121-best-time-to-buy-and-sell-stock)
- [136. Single Number](#136-single-number)
- [243. Shortest Word Distance](#243-shortest-word-distance)
  - [Approach #1 (Brute-force)](#approach-1-brute-force)
  - [Approach #2 (One-pass)](#approach-2-one-pass)
  - [Why not a while loop?](#why-not-a-while-loop)
- [268. Missing Number](#268-missing-number)
- [771. Jewels and Stones](#771-jewels-and-stones)
- [867. Transpose Matrix](#867-transpose-matrix)
- [1207. Unique Number of Occurrences](#1207-unique-number-of-occurrences)
- [1431. Kids With the Greatest Number of Candies](#1431-kids-with-the-greatest-number-of-candies)
- [1684. Count the Number of Consistent Strings](#1684-count-the-number-of-consistent-strings)
- [1732. Find the Highest Altitude](#1732-find-the-highest-altitude)
- [1773. Count Items Matching a Rule](#1773-count-items-matching-a-rule)
- [1816. Truncate Sentence](#1816-truncate-sentence)
- [1920. Build Array from Permutation](#1920-build-array-from-permutation)
- [1929. Concatenation of Array](#1929-concatenation-of-array)
- [2011. Final Value of Variable After Performing Operations](#2011-final-value-of-variable-after-performing-operations)
- [2185. Counting Words With a Given Prefix](#2185-counting-words-with-a-given-prefix)
- [2114. Maximum Number of Words Found in Sentences](#2114-maximum-number-of-words-found-in-sentences)
- [2535. Difference Between Element Sum and Digit Sum of an Array](#2535-difference-between-element-sum-and-digit-sum-of-an-array)
- [2798. Number of Employees Who Met the Target](#2798-number-of-employees-who-met-the-target)
- [2828. Check if a String Is an Acronym of Words](#2828-check-if-a-string-is-an-acronym-of-words)
- [3028. Ant on the Boundary](#3028-ant-on-the-boundary)


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


### 268. Missing Number
https://leetcode.com/problems/missing-number/

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        
        nums.sort()
        exp = [x for x in range(min(nums),len(nums)+1)]
        
        return sum(exp)-sum(nums)
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

### 1207. Unique Number of Occurrences
https://leetcode.com/problems/unique-number-of-occurrences/

```python
class Solution:
    def uniqueOccurrences(self, arr: List[int]) -> bool:
        
        occurences = {}

        # put count in dictionary
        for x in arr:
            if x not in occurences:
                occurences[x] = 0 

        # count occurences
        for x in arr:
            if x in occurences:
                occurences[x] += 1 

        occurences_list = []
        for x in occurences.values():
            occurences_list.append(x)

        occurences_list.sort()
        
        unique = list(set(occurences_list))
        unique.sort()

        # then use set
        return occurences_list == unique
```

### 1431. Kids With the Greatest Number of Candies
https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/

```python
class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:

        maxCandies = max(candies)
        result = []

        for candy in candies:
            if candy + extraCandies >= maxCandies:
                result.append(True)
            else:
                result.append(False) 
        
        return result
```

### 1684. Count the Number of Consistent Strings
https://leetcode.com/problems/count-the-number-of-consistent-strings/

```python
class Solution:
    def countConsistentStrings(self, allowed: str, words: List[str]) -> int:
        
        # counter, we are going to count when it breaks
        consistent_strings = len(words)

        # iterate through words
        for word in words:
            print(word)
            
            # set iterator
            i = 0 

            #check if letters in allowed
            while i in range(len(word)):
                # if it is not allowd, go to next word and remove 1 from count
                if word[i] not in allowed:
                    consistent_strings -= 1 
                    break
                i += 1 

        return consistent_strings
```

### 1732. Find the Highest Altitude
https://leetcode.com/problems/find-the-highest-altitude/

```python
class Solution:
    def largestAltitude(self, gain: List[int]) -> int:
        
        max_altitude = 0 
        total_gain = 0

        for x in range(len(gain)):
            total_gain += gain[x]

            if total_gain > max_altitude:
                max_altitude = total_gain
            else:
                pass
        
        return max_altitude
```

### 1773. Count Items Matching a Rule
https://leetcode.com/problems/count-items-matching-a-rule/

```python
class Solution:
    def countMatches(self, items: List[List[str]], ruleKey: str, ruleValue: str) -> int:
        
        item_match = 0

        for x in items:
            if ruleKey == 'type' and x[0] == ruleValue:
                item_match += 1 
            elif ruleKey == 'color' and x[1] == ruleValue:
                item_match += 1 
            elif ruleKey == 'name' and x[2] == ruleValue:
                item_match += 1 
            else:
                pass
        
        return item_match
```

### 1816. Truncate Sentence
https://leetcode.com/problems/truncate-sentence/

```python
class Solution:
    def truncateSentence(self, s: str, k: int) -> str:
        
        truncated = []

        for word in range(0,k):
            truncated.append(s.split()[word])
        
        return " ".join(truncated)
```

### 1920. Build Array from Permutation
https://leetcode.com/problems/build-array-from-permutation/

```python
class Solution:
    def buildArray(self, nums: List[int]) -> List[int]:
        
        ans = []
        
        for i in nums:
            ans.append(nums[i])

        return ans
```

### 1929. Concatenation of Array
https://leetcode.com/problems/concatenation-of-array/

lol this is faster tho

```python
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        return nums * 2
```
Second solution 

1. create empy list of certain length to avoid out of range errors
2. n is the increment to add to the index, based on original list length

```python
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:

        ans = [None] * len(nums)*2
        print(ans)
        n = len(nums)

        for i in range(len(nums)):
            print(nums[i])

            ans[i] = nums[i]
            ans[i + n] = nums[i]
    
        return ans
```
**Considerations:**
You cannot assign to a list like `xs[i] = value`, unless the list already is initialized with at least `i+1` elements. 

Instead, use `xs.append(value)` to add elements to the end of the list. (Though you could use the assignment notation if you were using a dictionary instead of a list.)

**Creating an empty list:**

```python
xs = [None] * 10
 xs
[None, None, None, None, None, None, None, None, None, None]
```

**Assigning a value to an existing element of the above list:**
```python
xs[1] = 5
xs
[None, 5, None, None, None, None, None, None, None, None]
```

### 2011. Final Value of Variable After Performing Operations
https://leetcode.com/problems/final-value-of-variable-after-performing-operations/

```python
class Solution:
    def finalValueAfterOperations(self, operations: List[str]) -> int:
        
        final_value = 0 
        
        for x in range(len(operations)):
            
            if operations[x] == '++X' or operations[x] == 'X++':
                final_value += 1 
            else:
                final_value -= 1 
            
        return final_value

```

### 2185. Counting Words With a Given Prefix
https://leetcode.com/problems/counting-words-with-a-given-prefix/

```python
class Solution:
    def prefixCount(self, words: List[str], pref: str) -> int:

        pref_len = len(pref)
        prefix_count = 0

        # cut the word to the prefx since we don't need to iterate through the whole thing
        for word in words:
            print(word[:pref_len])
            if word[:pref_len] == pref:
                prefix_count += 1 
        
        return prefix_count

```

### 2114. Maximum Number of Words Found in Sentences 
https://leetcode.com/problems/maximum-number-of-words-found-in-sentences/

```python
class Solution:
    def mostWordsFound(self, sentences: List[str]) -> int:
        
        max_words = 0

        for x in range(len(sentences)):
            if len(sentences[x].split()) >= max_words:
                max_words = len(sentences[x].split())

        return max_words

```

### 2535. Difference Between Element Sum and Digit Sum of an Array
https://leetcode.com/problems/difference-between-element-sum-and-digit-sum-of-an-array/

```python
class Solution:
    def differenceOfSum(self, nums: List[int]) -> int:
        element_sum = 0

        digit_sum = 0

        for x in range(len(nums)):
            element_sum += nums[x]
        
        for x in range(len(nums)):
            num_string = str(nums[x])
            for letter in num_string:
                digit_sum += int(letter)

        return element_sum - digit_sum
```

### 2798. Number of Employees Who Met the Target
https://leetcode.com/problems/number-of-employees-who-met-the-target/

```python
class Solution:
    def numberOfEmployeesWhoMetTarget(self, hours: List[int], target: int) -> int:
        
        MetTarget = 0

        for x in range(len(hours)):
            if hours[x] >= target:
                MetTarget += 1 
        
        return MetTarget
```

### 2828. Check if a String Is an Acronym of Words
https://leetcode.com/problems/check-if-a-string-is-an-acronym-of-words/

```python
class Solution:
    def isAcronym(self, words: List[str], s: str) -> bool:
        return "".join([word[0] for word in words] ) == s
```


### 3028. Ant on the Boundary
https://leetcode.com/problems/ant-on-the-boundary/description/

```python
class Solution:
    def returnToBoundaryCount(self, nums: List[int]) -> int:
        
        boundary = 0
        counter = 0

        for x in nums:
            boundary += x
            if boundary == 0:
                counter += 1 

        return counter
```