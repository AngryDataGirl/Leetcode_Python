
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

        #     j

        # a h b g d c

        #           i

  

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

  
