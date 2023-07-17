# Programming Skills

## Simulation

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
