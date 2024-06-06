- [1051. Height Checker](#1051-height-checker)
- [1160. Find Words That Can Be Formed by Characters](#1160-find-words-that-can-be-formed-by-characters)
- [1196. How Many Apples Can You Put into the Basket](#1196-how-many-apples-can-you-put-into-the-basket)
- [1207. Unique Number of Occurrences](#1207-unique-number-of-occurrences)
- [1287. Element Appearing More Than 25% In Sorted Array](#1287-element-appearing-more-than-25-in-sorted-array)
- [1313. Decompress Run-Length Encoded List](#1313-decompress-run-length-encoded-list)
- [1389. Create Target Array in the Given Order](#1389-create-target-array-in-the-given-order)
- [1431. Kids With the Greatest Number of Candies](#1431-kids-with-the-greatest-number-of-candies)
- [1436. Destination City](#1436-destination-city)
- [1464. Maximum Product of Two Elements in an Array](#1464-maximum-product-of-two-elements-in-an-array)
- [1637. Widest Vertical Area Between Two Points Containing No Points](#1637-widest-vertical-area-between-two-points-containing-no-points)
- [1684. Count the Number of Consistent Strings](#1684-count-the-number-of-consistent-strings)
- [1732. Find the Highest Altitude](#1732-find-the-highest-altitude)
- [1748. Sum of Unique Elements](#1748-sum-of-unique-elements)
- [1773. Count Items Matching a Rule](#1773-count-items-matching-a-rule)
- [1816. Truncate Sentence](#1816-truncate-sentence)
- [1854. Maximum Population Year](#1854-maximum-population-year)
- [1913. Maximum Product Difference Between Two Pairs](#1913-maximum-product-difference-between-two-pairs)
- [1920. Build Array from Permutation](#1920-build-array-from-permutation)
- [1929. Concatenation of Array](#1929-concatenation-of-array)


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

### 1196. How Many Apples Can You Put into the Basket
https://leetcode.com/problems/how-many-apples-can-you-put-into-the-basket/

```python
class Solution:
    def maxNumberOfApples(self, weight: List[int]) -> int:
        
        weight.sort() 

        BasketVol= 5000
        NumOfApples = 0 
        
        for x in range(len(weight)):
            if weight[x] <= BasketVol and BasketVol - weight[x] >= 0:
                BasketVol -= weight[x]
                NumOfApples += 1         
        return NumOfApples
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

### 1313. Decompress Run-Length Encoded List
https://leetcode.com/problems/decompress-run-length-encoded-list/

```python
class Solution:
    def decompressRLElist(self, nums: List[int]) -> List[int]:
        
        RLElist = []

        for x in range(0,len(nums),2):
            freq = nums[x]
            val = [nums[x+1]]

            for x in val*freq:
                RLElist.append(x)

        return RLElist
```

### 1389. Create Target Array in the Given Order
https://leetcode.com/problems/create-target-array-in-the-given-order/

```python
class Solution:
    def createTargetArray(self, nums: List[int], index: List[int]) -> List[int]:
        
        target = []

        for i in range(len(nums)):
            target.insert(index[i], nums[i])

        return target
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

### 1854. Maximum Population Year
https://leetcode.com/problems/maximum-population-year/

```python
class Solution:
    def maximumPopulation(self, logs: List[List[int]]) -> int:

       # find max and min years
        years = []
        for x in range(len(logs)):
            # print(logs[x][0], logs[x][1])
            years.append(logs[x][0])
            years.append(logs[x][1])

        min_year = min(years)
        max_year = max(years)

        # variables to store max pop and earliest year 
        max_pop = 0
        earliest_year = min_year

        # loop through years to check pop
        for y in range(min_year, max_year):
            pop = 0

            print(y)

            for x in range(len(logs)):
                birth = logs[x][0]
                death = logs[x][1]

                if birth <= y and death > y :
                    pop += 1 

            if pop > max_pop:
                max_pop = pop
                if y > earliest_year:
                    earliest_year = y

            # print("year",y,"population",pop, max_pop, earliest_year)

        return earliest_year
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
