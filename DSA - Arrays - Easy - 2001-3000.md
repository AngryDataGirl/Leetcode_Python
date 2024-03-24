- [2011. Final Value of Variable After Performing Operations](#2011-final-value-of-variable-after-performing-operations)
- [2089. Find Target Indices After Sorting Array](#2089-find-target-indices-after-sorting-array)
- [2185. Counting Words With a Given Prefix](#2185-counting-words-with-a-given-prefix)
- [2114. Maximum Number of Words Found in Sentences](#2114-maximum-number-of-words-found-in-sentences)
- [2303. Calculate Amount Paid in Taxes](#2303-calculate-amount-paid-in-taxes)
- [2418. Sort the People](#2418-sort-the-people)
- [2446. 2446. Determine if Two Events Have Conflict](#2446-2446-determine-if-two-events-have-conflict)
- [2535. Difference Between Element Sum and Digit Sum of an Array](#2535-difference-between-element-sum-and-digit-sum-of-an-array)
- [2660. Determine the Winner of a Bowling Game](#2660-determine-the-winner-of-a-bowling-game)
- [2678. Number of Senior Citizens](#2678-number-of-senior-citizens)
- [2706. Buy Two Chocolates](#2706-buy-two-chocolates)
- [2733. Neither Minimum nor Maximum](#2733-neither-minimum-nor-maximum)
- [2798. Number of Employees Who Met the Target](#2798-number-of-employees-who-met-the-target)
- [2828. Check if a String Is an Acronym of Words](#2828-check-if-a-string-is-an-acronym-of-words)
- [2951. Find the Peaks](#2951-find-the-peaks)
- [3005. Count Elements With Maximum Frequency](#3005-count-elements-with-maximum-frequency)
- [3028. Ant on the Boundary](#3028-ant-on-the-boundary)
- [3074. Apple Redistribution into Boxes](#3074-apple-redistribution-into-boxes)

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

### 2303. Calculate Amount Paid in Taxes
https://leetcode.com/problems/calculate-amount-paid-in-taxes/ 

```python
class Solution:
    def calculateTax(self, brackets: List[List[int]], income: int) -> float:

        total_tax = 0
        last_bracket = 0

        for x in range(len(brackets)):
            
            tax_rate = brackets[x][1]/100
            curr_bracket = brackets[x][0]
            # print("[", last_bracket,",", curr_bracket,"]","tax rate",tax_rate,"income", income)
            
            taxable_income = min(curr_bracket, income)-last_bracket
            # print("taxable income",taxable_income)
            if taxable_income > 0 :
                tax = taxable_income * tax_rate
                # print(tax)
                total_tax += tax 
                last_bracket = curr_bracket

            else:
                break
        return total_tax 
```

### 2418. Sort the People
https://leetcode.com/problems/sort-the-people/
```python
class Solution:
    def sortPeople(self, names: List[str], heights: List[int]) -> List[str]:
        
        people = []

        for x in range(len(names)):
            person = [heights[x],names[x]]
            people.append(person)

        people.sort(reverse = True)

        sortedPeople = []
        for x in people:
            sortedPeople.append(x[1])
            
        return sortedPeople
```

### 2446. 2446. Determine if Two Events Have Conflict
https://leetcode.com/problems/determine-if-two-events-have-conflict/

```python
class Solution:
    def haveConflict(self, event1: List[str], event2: List[str]) -> bool:
        
        if event1[0] > event2[1]:
            return False
        elif event1[1] >= event2[0]:
            return True
        else:
            return False
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

### 2660. Determine the Winner of a Bowling Game
https://leetcode.com/problems/determine-the-winner-of-a-bowling-game/

```sql
class Solution:
    def isWinner(self, player1: List[int], player2: List[int]) -> int:
        
        def score(player):
            score = 0
            for x in range(len(player)):
                # print("index: ",x)
                if (x >= 1 and player[x-1] == 10) or (x >= 2 and player[x-2] == 10):
                    score += 2*player[x]
                    # print(2*player[x],"doubled, added to score")
                else:
                    score += player[x]
                    # print(player[x],"added to score")
            return score
        
        p1 = score(player1)
        # print("player1 score",p1)

        p2 = score(player2)
        # print("player2 score",p2)
        
        if p1 > p2:
            return 1
        elif p1 < p2:
            return 2 
        else:
            return 0
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

### 3005. Count Elements With Maximum Frequency
https://leetcode.com/problems/count-elements-with-maximum-frequency/

```python
class Solution:
    def maxFrequencyElements(self, nums: List[int]) -> int:
        
        freqdict = {}
        sum = 0 

        for x in range(len(nums)):
            if nums[x] not in freqdict:
                freqdict[nums[x]] = 1
            else:
                freqdict[nums[x]] += 1 

        maxcount = freqdict[max(freqdict, key=freqdict.get)]

        keys = [k for k, v in freqdict.items() if v == maxcount]

        for key, value in freqdict.items():
            if key in keys:
                print(value)
                sum = value + sum

        return sum
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

### 3074. Apple Redistribution into Boxes
https://leetcode.com/problems/apple-redistribution-into-boxes/

```python
class Solution:
    def minimumBoxes(self, apple: List[int], capacity: List[int]) -> int:
        
        # sort the boxes by capacity , biggest box first 
        capacity.sort(reverse=True)

        # store variables
        min_boxes = 0
        sum_capacity = 0
        i = 0

        # loop  
        while i < len(capacity) and sum_capacity < sum(apple):
            min_boxes += 1 
            sum_capacity += capacity[i]
            i += 1 

        return min_boxes
```