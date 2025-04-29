# EX 3A Knight Tour & Count Path
## DATE: 18.03.2025
## AIM:
To write a python program to find minimum steps to reach to specific cell in minimum moves by knight

## Algorithm:

1. Define a `cell` class to represent a position `(x, y)` and distance `dist` from the starting point.  
2. Define `isInside(x, y, N)` to check if the cell `(x, y)` lies inside the `N x N` chessboard.  
3. Define `minStepToReachTarget(knightpos, targetpos, N)` to find the minimum steps using BFS.  
4. Initialize lists `dx` and `dy` to represent all 8 possible knight moves.  
5. Create a queue and enqueue the starting position with distance 0.  
6. Create a 2D list `visited` to track visited cells and mark the starting cell as visited.  
7. While the queue is not empty, dequeue a cell `t` and check if it matches the target.  
8. If target reached, return the distance `t.dist`.  
9. Otherwise, loop over all 8 possible knight moves from the current cell.  
10. For each valid and unvisited move `(x, y)`, mark it visited and enqueue it with incremented distance.  
11. In the main block, define board size `N`, starting `knightpos`, and `targetpos`.  
12. Call `minStepToReachTarget()` and print the result (minimum steps required).  

## Program:
```
/*
Program to implement to find minimum steps to reach to specific cell in minimum moves by knight.
Developed by: AKSHAYAA M
Register Number: 212222230009
*/
```
```python
class cell:
     
    def __init__(self, x = 0, y = 0, dist = 0):
        self.x = x
        self.y = y
        self.dist = dist

def isInside(x, y, N):
    if (x >= 1 and x <= N and
        y >= 1 and y <= N):
        return True
    return False
def minStepToReachTarget(knightpos,
                         targetpos, N):
                             
    dx = [2, 2, -2, -2, 1, 1, -1, -1]
    dy = [1, -1, 1, -1, 2, -2, 2, -2]
 
    queue = []
 
    # push starting position of knight
    # with 0 distance
    queue.append(cell(knightpos[0], knightpos[1], 0))
 
    # make all cell unvisited
    visited = [[False for i in range(N + 1)]
               for j in range(N + 1)]
 
    # visit starting state
    visited[knightpos[0]][knightpos[1]] = True
 
    # loop until we have one element in queue
    while(len(queue) > 0):
 
        t = queue[0]
        queue.pop(0)
 
        # if current cell is equal to target
        # cell, return its distance
        if(t.x == targetpos[0] and
           t.y == targetpos[1]):
            return t.dist
 
        # iterate for all reachable states
        for i in range(8):
 
            x = t.x + dx[i]
            y = t.y + dy[i]
 
            if(isInside(x, y, N) and not visited[x][y]):
                visited[x][y] = True
                queue.append(cell(x, y, t.dist + 1))
     

    
if __name__=='__main__':
    N = 30
    knightpos = [1, 1]
    targetpos = [30, 30]
    print(minStepToReachTarget(knightpos,
                               targetpos, N))
```

## Output:

![image](https://github.com/user-attachments/assets/db72fd25-e989-4042-9f20-260b6b304869)


## Result:
The program executed successfully, and the minimum number of steps for the knight to reach the target was calculated.
