  
#PrefixSum #DSA #Leetcode 

It is a derived array that stores the cumulative sum of elements in a given array.
  
**How does it work?** 
Let's say you have a list of numbers: [a, b, c, d, e]. 
The prefix sum list would be: [a, a+b, a+b+c, a+b+c+d, a+b+c+d+e].
 
**Why is it useful?**
Once you have computed the prefix sum list, you can quickly find the sum of any subrange of elements in the original list using just `two index lookups and a subtraction`. This is much more efficient than repeatedly summing the elements in the subrange.
 
 **Example of Use:** If you want to find the sum of elements from index i to index j (where j is greater than i) in the original list, you can simply subtract prefixSum[i-1] from prefixSum[j] (if i > 0, otherwise it's just prefixSum[j]). 
 
 Suppose we have the original list: `nums = [1, 2, 3, 4, 5]`, and we have computed the prefix sum list: `prefix_sum = [0, 1, 3, 6, 10, 15]`.

Now, let's say we want to find the sum of elements from index `i = 2` to index `j = 4` in the original list `nums`.

Here's how we can do it using prefix sums:

1. First, we get the prefix sum of the element at index `i - 1` and index `j` in the prefix sum list.
2. So, `prefix_sum[i - 1]` gives us the prefix sum at index `i - 1 = 1` which is `1`.
3. And `prefix_sum[j]` gives us the prefix sum at index `j = 4` which is `10`.
4. Then, we subtract `prefix_sum[i - 1]` from `prefix_sum[j]`.
5. So, `prefix_sum[j] - prefix_sum[i - 1] = 10 - 1 = 9`.

Therefore, the sum of elements from index 2 to index 4 in the original list `nums` is `9`.

 **Important Note:** You might notice that to compute prefix sums efficiently, it's good to have a placeholder at the beginning of the prefix sum list, often 0. This is because it helps simplify the computation for the first element's prefix sum (which is just the element itself).
# Intuition

1. Initialize an array, say prefixSum[], of the same length as the input array.
2. Set the first element of the prefixSum[] as the same as the first element of the input array.
3. Iterate through the input array starting from the second element.
4. For each element, calculate the prefix sum by adding the current element with the prefix sum value of the previous index.
5. Assign the prefix sum value to the corresponding index in the prefixSum array.
6. Repeat steps 3–5 until the end of the input array is reached.
# Template
  

```python

def fn(arr):

    prefix = [arr[0]]

    for i in range(1, len(arr)):

        prefix.append(prefix[-1] + arr[i])

    return prefix

```

  