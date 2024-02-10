- [136. Single Number](#136-single-number)
- [268. Missing Number](#268-missing-number)
- [867. Transpose Matrix](#867-transpose-matrix)
- [1207. Unique Number of Occurrences](#1207-unique-number-of-occurrences)
- [1431. Kids With the Greatest Number of Candies](#1431-kids-with-the-greatest-number-of-candies)
- [1684. Count the Number of Consistent Strings](#1684-count-the-number-of-consistent-strings)
- [1732. Find the Highest Altitude](#1732-find-the-highest-altitude)
- [1773. Count Items Matching a Rule](#1773-count-items-matching-a-rule)
- [1816. Truncate Sentence](#1816-truncate-sentence)
- [1920. Build Array from Permutation](#1920-build-array-from-permutation)
- [2011. Final Value of Variable After Performing Operations](#2011-final-value-of-variable-after-performing-operations)
- [2185. Counting Words With a Given Prefix](#2185-counting-words-with-a-given-prefix)
- [2114. Maximum Number of Words Found in Sentences](#2114-maximum-number-of-words-found-in-sentences)
- [2535. Difference Between Element Sum and Digit Sum of an Array](#2535-difference-between-element-sum-and-digit-sum-of-an-array)
- [2798. Number of Employees Who Met the Target](#2798-number-of-employees-who-met-the-target)
- [2828. Check if a String Is an Acronym of Words](#2828-check-if-a-string-is-an-acronym-of-words)
- [3028. Ant on the Boundary](#3028-ant-on-the-boundary)

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

### 268. Missing Number
https://leetcode.com/problems/missing-number/

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        
        nums.sort()
        exp = [x for x in range(min(nums),len(nums)+1)]
        
        return sum(exp)-sum(nums)
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