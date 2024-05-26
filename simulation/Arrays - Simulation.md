#Leetcode #Python #Simulation #Easy
# 682. Baseball Game
https://leetcode.com/problems/baseball-game/

```python
class Solution:
    def calPoints(self, operations: List[str]) -> int:

        starting_score = []
        print(starting_score)

        for x in range(len(operations)):
            if operations[x].lstrip("-").isdigit() == True:
                starting_score.append(int(operations[x]))
                # print(starting_score)
            if operations[x] == "C":
                starting_score.pop()
                # print(starting_score)
            if operations[x] == "D":
                starting_score.append(int((starting_score[-1]))*2)
                # print(starting_score)
            if operations[x] == "+":
                starting_score.append(int(starting_score[-1]) + int(starting_score[-2]))
                # print(starting_score)

        return sum(starting_score)
```

# 657. Robot Return to Origin
https://leetcode.com/problems/robot-return-to-origin/

```python
class Solution:
    def judgeCircle(self, moves: str) -> bool:
        
        # move values dictionary
        moves_dict = {
            'L' : [-1,0],
            'U' : [0,1],
            'R' : [1,0],
            'D' : [0,-1]
        }

        print(moves_dict)

        # robots starting position
        start_coords = [0,0]

        for x in range(len(moves)):
            movement = moves_dict[moves[x]]
            start_coords[0] += movement[0]
            start_coords[1] += movement[1]
        
        if start_coords == [0,0]:
            return True
        else:
            return False
```

# [2357. Make Array Zero by Subtracting Equal Amounts
[2357. Make Array Zero by Subtracting Equal Amounts](https://leetcode.com/problems/make-array-zero-by-subtracting-equal-amounts/)

wordy solution
```python
class Solution:

    def minimumOperations(self, nums: List[int]) -> int:
        counter = 0
  
        while set(nums) != {0}:

            choose_x = [x for x in nums if x != 0]
            min_x = min(choose_x)

              for x in range(len(nums)):
                if nums[x] >= min_x:
                    nums[x] = nums[x] - min_x
            counter += 1

        return counter
```

The answer is the number of unique non-zero numbers in nums.

```python
class Solution:
    def minimumOperations(self, nums: List[int]) -> int:
        nums = list(set(nums))

        for x in nums:
            if x == 0:
                nums.pop(x)

        return len(nums)
```
# 2660. Determine the Winner of a Bowling Game
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
