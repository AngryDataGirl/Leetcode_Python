#Concepts


```python

def fn(arr):

    def dp(STATE):

        if BASE_CASE:

            return 0

        if STATE in memo:

            return memo[STATE]

        ans = RECURRENCE_RELATION(STATE)

        memo[STATE] = ans

        return ans

  

    memo = {}

    return dp(STATE_FOR_WHOLE_INPUT)

```

  
# What is Dynamic Programming
- solve complex problems by breaking them down into simpler subproblems
- subproblems 1 time and store results so you do not have to compute again 
- the solutions to the subproblems are stored thereby avoiding redundant compuation where we see repeated calls for the same inputs
- this reduces time complexities from exponential to polynomial
- can be implemented using recursion: where solutions to subproblems are found recursively, or iteratively, where solutions to subproblems are found in a specific order 

## What is the difference between a Dynamic programming algorithm and recursion?

- **dynamic programming**, problems are solved by breaking them down into smaller ones to solve the larger ones
- **recursion**** is when a function is called and executed by itself. 

- Therefore, the main difference between the two techniques is their intended use; ****recursion**** is used to automate a function, whereas dynamic programming is an optimization technique used to solve problems.

## Techniques to solve Dynamic Programming Problems:

### 1. Top-Down(Memoization):

1. Break down the given problem in order to begin solving it. 
2. If you see that the problem has already been solved, return the saved answer. 
3. If it hasn’t been solved, solve it and save it. 

This is usually easy to think of and very intuitive, This is referred to as [Memoization](https://www.geeksforgeeks.org/memoization-1d-2d-and-3d/).

### 2. Bottom-Up(Tabulation):

1/ Analyze the problem and see in what order the subproblems are solved, and work your way up from the trivial subproblem to the given problem. 
This process ensures that the subproblems are solved before the main problem. This is referred to as [Dynamic Programming](http://www.geeksforgeeks.org/dynamic-programming/).