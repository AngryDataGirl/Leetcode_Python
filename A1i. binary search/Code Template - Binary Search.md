
# Duplicate elements, right most insertion point

```python

def fn(arr, target):

    left = 0

    right = len(arr)

    while left < right:

        mid = (left + right) // 2

        if arr[mid] > target:

            right = mid

        else:

            left = mid + 1

  

    return left

```

# Duplicate elements, left most insertion point


```python

def fn(arr, target):

    left = 0

    right = len(arr)

    while left < right:

        mid = (left + right) // 2

        if arr[mid] >= target:

            right = mid

        else:

            left = mid + 1

  

    return left

```

  
