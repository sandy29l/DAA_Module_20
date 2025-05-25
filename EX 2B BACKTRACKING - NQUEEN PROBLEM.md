# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE:08.03.2025
## AIM:
To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.

## Algorithm:
```
1.Input the value of N (size of the board and number of queens)
2.Create a 2D board of size N × N initialized with 0
 • A 1 will represent a queen, and 0 will represent an empty cell
3. Define isSafe(board, row, col) to check if placing a queen is valid
 • Check the left side of the current row for another queen
 • Check the upper-left diagonal for another queen
 • Check the lower-left diagonal for another queen
 • If all are safe, return True, else return False
4.Define the recursive function solveNQUtil(board, col)
 • Base case: If col >= N, all queens are placed successfully → return True
 • For each row i from 0 to N-1:
  – Check if placing a queen at board[i][col] is safe using isSafe()
  – If safe:
• Place the queen → set board[i][col] = 1
   • Recur to place rest of the queens → call solveNQUtil(board, col + 1)
   • If recursion returns True, return True
   • Else (backtrack): Remove the queen → set board[i][col] = 0
 • If no row is valid in current column, return False

5.Define solveNQ()
 • Create the initial board of N × N zeros
 • Call solveNQUtil(board, 0)
  – If it returns True, call printSolution(board) to display result
  – Else, print "Solution does not exist"
```


## Program:
```

Program to implement N-Queen problem using backtracking.
Developed by: SANTHOSH L
Register Number:  212222100046
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
    if col>=N:
           return True
    for i in range(N):
        if isSafe(board,i,col):
            board[i][col]=1
            if solveNQUtil(board, col+1)==True:
                return True
            board[i][col]=0
    return False
                
        
        
        
def solveNQ():
    board = [ [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0]]
              
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()

```

## Output:
![Screenshot 2025-04-29 113548](https://github.com/user-attachments/assets/914d40d3-aafb-4fdd-980f-8cdd8a85c1d8)

## Result:
The N-Queens program executed successfully, and a valid board configuration was generated.
