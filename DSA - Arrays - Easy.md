- [1. Two Sum](#1-two-sum)
- [121. Best Time to Buy and Sell Stock](#121-best-time-to-buy-and-sell-stock)
- [136. Single Number](#136-single-number)
- [243. Shortest Word Distance](#243-shortest-word-distance)
  - [Approach #1 (Brute-force)](#approach-1-brute-force)
  - [Approach #2 (One-pass)](#approach-2-one-pass)
  - [Why not a while loop?](#why-not-a-while-loop)
- [268. Missing Number](#268-missing-number)
- [500. Keyboard Row](#500-keyboard-row)
- [771. Jewels and Stones](#771-jewels-and-stones)
- [804. Unique Morse Code Words](#804-unique-morse-code-words)
- [819. Most Common Word](#819-most-common-word)
- [867. Transpose Matrix](#867-transpose-matrix)
- [929. Unique Email Addresses](#929-unique-email-addresses)
- [1051. Height Checker](#1051-height-checker)
- [1160. Find Words That Can Be Formed by Characters](#1160-find-words-that-can-be-formed-by-characters)
- [1207. Unique Number of Occurrences](#1207-unique-number-of-occurrences)
- [1287. Element Appearing More Than 25% In Sorted Array](#1287-element-appearing-more-than-25-in-sorted-array)
- [1431. Kids With the Greatest Number of Candies](#1431-kids-with-the-greatest-number-of-candies)
- [1436. Destination City](#1436-destination-city)
- [1464. Maximum Product of Two Elements in an Array](#1464-maximum-product-of-two-elements-in-an-array)
- [1637. Widest Vertical Area Between Two Points Containing No Points](#1637-widest-vertical-area-between-two-points-containing-no-points)
- [1684. Count the Number of Consistent Strings](#1684-count-the-number-of-consistent-strings)
- [1732. Find the Highest Altitude](#1732-find-the-highest-altitude)
- [1748. Sum of Unique Elements](#1748-sum-of-unique-elements)
- [1773. Count Items Matching a Rule](#1773-count-items-matching-a-rule)
- [1816. Truncate Sentence](#1816-truncate-sentence)
- [1913. Maximum Product Difference Between Two Pairs](#1913-maximum-product-difference-between-two-pairs)
- [1920. Build Array from Permutation](#1920-build-array-from-permutation)
- [1929. Concatenation of Array](#1929-concatenation-of-array)
- [2011. Final Value of Variable After Performing Operations](#2011-final-value-of-variable-after-performing-operations)
- [2089. Find Target Indices After Sorting Array](#2089-find-target-indices-after-sorting-array)
- [2185. Counting Words With a Given Prefix](#2185-counting-words-with-a-given-prefix)
- [2114. Maximum Number of Words Found in Sentences](#2114-maximum-number-of-words-found-in-sentences)
- [2535. Difference Between Element Sum and Digit Sum of an Array](#2535-difference-between-element-sum-and-digit-sum-of-an-array)
- [2678. Number of Senior Citizens](#2678-number-of-senior-citizens)
- [2706. Buy Two Chocolates](#2706-buy-two-chocolates)
- [2733. Neither Minimum nor Maximum](#2733-neither-minimum-nor-maximum)
- [2798. Number of Employees Who Met the Target](#2798-number-of-employees-who-met-the-target)
- [2828. Check if a String Is an Acronym of Words](#2828-check-if-a-string-is-an-acronym-of-words)
- [2951. Find the Peaks](#2951-find-the-peaks)
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

### 1051. Height Checker
https://leetcode.com/problems/height-checker/

```python
class Solution:
    def heightChecker(self, heights: List[int]) -> int:
        
        sorted_heights = [x for x in heights]
        sorted_heights.sort()

        counter = 0
        for x in range(len(heights)):
            if heights[x] != sorted_heights[x]:
                counter += 1 
        
        return counter
```

### 1160. Find Words That Can Be Formed by Characters
https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/

```python
class Solution:
    def countCharacters(self, words: List[str], chars: str) -> int:

        chars_dict = {}

        # create the dictionary   
        def char_dict_function():     
            for x in chars:
                if x not in chars_dict:
                    chars_dict[x] = 0    
            for x in chars:
                if x in chars_dict:
                    chars_dict[x] += 1 

        char_dict_function()

        # empty list for result words
        good_words = []

        # loop through words list 
        for word in range(len(words)):  
            i = 0 
            while i < len(words[word]) :

                if words[word][i] in chars_dict and chars_dict[words[word][i]] > 0:
                    chars_dict[words[word][i]] -= 1                    
                else:
                    break
                i += 1 

                if i == len(words[word]):
                    good_words.append(words[word])
                    
                #     print(chars_dict)
            chars_dict = {}
            char_dict_function()

        return len("".join(good_words))
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

### 1287. Element Appearing More Than 25% In Sorted Array
https://leetcode.com/problems/element-appearing-more-than-25-in-sorted-array/

```python
class Solution:
    def findSpecialInteger(self, arr: List[int]) -> int:
        
        count = len(arr)/ 4 

        dict = {}

        for x in arr:
            if x not in dict:
                dict[x] = 0 

        for x in arr:
            if x in dict:
                dict[x] += 1 

        for key, value in dict.items():
            if value > count:
                return key
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

### 1436. Destination City
https://leetcode.com/problems/destination-city/

```python
class Solution:
    def destCity(self, paths: List[List[str]]) -> str:
        
        destinations = []
        leaving_city = []

        for x in range(len(paths)):
            destinations.append(paths[x][1])
            leaving_city.append(paths[x][0])

        for x in range(len(destinations)):
            if destinations[x] not in leaving_city:
                
                return destinations[x]
```

### 1464. Maximum Product of Two Elements in an Array
https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array/

```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        nums.sort(reverse=True)
        return (nums[0]-1) * (nums[1]-1)
```

### 1637. Widest Vertical Area Between Two Points Containing No Points
https://leetcode.com/problems/widest-vertical-area-between-two-points-containing-no-points/

```python
class Solution:
    def maxWidthOfVerticalArea(self, points: List[List[int]]) -> int:
        
        x_list=[]
        
        for point in points:
            x_list.append(point[0])

        x_list.sort()

        widest_area = 0
        
        for x in range(len(x_list)-1):
             
            if x_list[x+1]-x_list[x] > widest_area:
                widest_area = x_list[x+1]-x_list[x]
        
        return widest_area
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

### 1748. Sum of Unique Elements
https://leetcode.com/problems/sum-of-unique-elements/

```python
class Solution:
    def sumOfUnique(self, nums: List[int]) -> int:
        unique_dict = {}
        sum_unique = 0

        for x in nums:
            if x not in unique_dict:
                unique_dict[x] = 0 
        
        for x in nums:
            if x in unique_dict:
                unique_dict[x] += 1 
        
        for x in unique_dict:
            if unique_dict[x] == 1:
                sum_unique += x
        
        return sum_unique
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

### 1913. Maximum Product Difference Between Two Pairs
https://leetcode.com/problems/maximum-product-difference-between-two-pairs/
 
```python
class Solution:
    def maxProductDifference(self, nums: List[int]) -> int:

        nums.sort()

        product1 = nums[len(nums)-1] * nums[len(nums)-2]        
        product2 = nums[0] * nums[1]

        return product1-product2
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

### 2089. Find Target Indices After Sorting Array
https://leetcode.com/problems/find-target-indices-after-sorting-array/

```python
class Solution:
    def targetIndices(self, nums: List[int], target: int) -> List[int]:
        
        nums.sort()

        target_indices = []
        
        for x in range(len(nums)):
            print(nums[x])
            if nums[x] == target:
                target_indices.append(x)

        return target_indices
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

### 2678. Number of Senior Citizens
https://leetcode.com/problems/number-of-senior-citizens/

```python
class Solution:
    def countSeniors(self, details: List[str]) -> int:
        counter = 0 

        for x in details:
            if int(x[11:13]) > 60:
                counter += 1 
        
        return counter
```

### 2706. Buy Two Chocolates
https://leetcode.com/problems/buy-two-chocolates/

```python
class Solution:
    def buyChoco(self, prices: List[int], money: int) -> int:

        prices.sort()

        if prices[0] + prices[1] <= money:
            return money - (prices[0] + prices[1])
        else:
            return money 
```

### 2733. Neither Minimum nor Maximum
https://leetcode.com/problems/neither-minimum-nor-maximum/

```python
class Solution:
    def findNonMinOrMax(self, nums: List[int]) -> int:
        
        for x in range(len(nums)):
            if nums[x] != max(nums) and nums[x] != min(nums):
                return nums[x]
             
        return -1
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

### 2951. Find the Peaks
https://leetcode.com/problems/find-the-peaks/

```python
class Solution:
    def findPeaks(self, mountain: List[int]) -> List[int]:
        
        peaks = []

        for x in range(1,len(mountain)-1):
            if mountain[x-1] < mountain[x] > mountain[x+1]:
                peaks.append(x)

        return peaks
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