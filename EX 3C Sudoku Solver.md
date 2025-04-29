# EX 3C Sudoku Solver
## DATE: 25.03.2025
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm:

1. Define the 9×9 Sudoku `board` with initial values (0 indicates empty cells).  
2. Create a function `printBoard(board)` to display the current board state row by row.  
3. Define `isPossible(board, row, col, val)` to check if placing `val` at `(row, col)` is valid.  
4. In `isPossible`, check if `val` is already in the same row or column; if so, return `False`.  
5. Calculate the top-left corner of the 3×3 subgrid containing `(row, col)`.  
6. Check if `val` exists in that 3×3 subgrid; if so, return `False`.  
7. If all checks pass, return `True` indicating `val` is valid for that cell.  
8. Define the recursive `solve()` function to fill the board using backtracking.  
9. Loop over all cells; if a cell is empty (`0`), try placing values `1` to `9`.  
10. For each value, if it is valid using `isPossible`, place it and recursively call `solve()`.  
11. After the recursive call, reset the cell to `0` to backtrack.  
12. If all cells are filled, call `printBoard()` to display the completed Sudoku.  
13. Start solving by calling `solve()` once at the end.  


## Program:
```
/*
Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: AKSHAYAA M
Register Number: 212222230009
*/
```
```python
board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    for i in range(0,9):
        for j in range(0,9):
            if board[i][j] == 0:
                for val in range(1,10):
                    if isPossible(board,i,j,val):
                        board[i][j]=val
                        solve()
                        board[i][j]=0
                return 
    printBoard(board)        
solve()
```

## Output:

![image](https://github.com/user-attachments/assets/e970db21-1325-4d87-a291-47fa84198921)


## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
