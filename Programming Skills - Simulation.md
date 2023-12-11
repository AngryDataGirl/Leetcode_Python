- [Programming Skills](#programming-skills)
  - [Simulation](#simulation)
    - [682. Baseball Game](#682-baseball-game)
    - [657. Robot Return to Origin](#657-robot-return-to-origin)


# Programming Skills

## Simulation

### 682. Baseball Game
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

### 657. Robot Return to Origin
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
