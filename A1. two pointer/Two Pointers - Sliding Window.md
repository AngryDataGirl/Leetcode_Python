
#SlidingWindow
#DSA #Loops
#Array 

**Window Sliding Technique** is a computational technique that aims to reduce the use of nested loops and replace it with a single loop, thereby reducing the time complexity.

**Prerequisite** 
Specific scenario required: 
1. the **size of the window** for computation is **fixed** throughout the complete nested loop. 

**How to Know, Where we use the Sliding Window?**

> [!Tip] 
> Usually these terms will be used: Array, String, Sub Array, Sub String, Largest Sum, Maximum Sum, Minimum Sum

**How to use Sliding Window Technique?**
1. Find the size of the window required 
2. Compute the result for 1st window, i.e. from the start of the data structure
3. Then use a loop to slide the window by 1, and keep computing the result window by window.

```python

def fn(arr):
    left = ans = curr = 0
  
    for right in range(len(arr)):
        # do logic here to add arr[right] to curr

        while WINDOW_CONDITION_BROKEN:
            # remove arr[left] from curr
            left += 1
        # update ans

    return ans

```

  