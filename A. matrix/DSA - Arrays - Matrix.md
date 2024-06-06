### 463. Island Perimeter
https://leetcode.com/problems/island-perimeter/

```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:

        max_x = len(grid[0])
        max_y = len(grid)

        perimeter = 0

        for row in range(max_y):
            print(grid[row])
            for col in range(max_x):
                if grid[row][col] == 1:
                    perimeter += 4
                    if row != 0:
                        if grid[row-1][col] == 1:
                            perimeter -= 1 
                    if row != max_y-1:
                        if grid[row+1][col] == 1:
                            perimeter -= 1
                    if col != 0:
                        if grid[row][col-1] == 1:
                            perimeter -= 1 
                    if col != max_x-1:
                        if grid[row][col+1] == 1:
                            perimeter -= 1        
        
        return perimeter                 
```

more efficient solution 

```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        rows = len(grid)
        cols = len(grid[0])
        
        result = 0
        
        for r in range(rows):
            for c in range(cols):
                if grid[r][c] == 1:
                    result += 4
                    
                    if r > 0 and grid[r-1][c] == 1:
                        result -= 2
                        
                    if c > 0 and grid[r][c-1] == 1:
                        result -= 2
        
        return result
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
