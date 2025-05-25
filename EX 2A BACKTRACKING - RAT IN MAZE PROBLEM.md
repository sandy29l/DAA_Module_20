# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:04.03.2025
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.

## Algorithm:
```
1.Define Constants
 • Let N be the size of the maze (e.g., 4 for a 4x4 maze)
 • maze[N][N] is a 2D list containing 0s and 1s
  – 1 indicates open path
  – 0 indicates wall or blocked cell

2.Create a solution matrix sol[N][N]
 • Initialize all values to 0
 • This will store the path taken by the rat

3.Define a function isSafe(maze, x, y)
 • Returns True if:
  – x and y are within maze boundaries
  – maze[x][y] == 1 (path is open)
 • Else, returns False
4.Define recursive function solveMazeUtil(maze, x, y, sol)
 • If x == N-1 and y == N-1:
  – Mark sol[x][y] = 1
  – Return True (destination reached)
 • Else:
  – Check if isSafe(maze, x, y) is True
  – Mark sol[x][y] = 1
  – Recur to the next cell in the down direction → (x+1, y)
    – If path exists, return True
  – Recur to the next cell in the right direction → (x, y+1)
    – If path exists, return True
  – If both directions fail:
    – Backtrack: Mark sol[x][y] = 0
    – Return False
5.Define solveMaze(maze)
 • Initialize solution matrix sol[N][N] with 0s
 • Call solveMazeUtil(maze, 0, 0, sol)
 • If solution exists:
  – Print the solution matrix sol
 • Else:
  – Print “Solution doesn't exist”

6.Input the maze and call solveMaze(maze)
``` 

## Program:
```

Program to implement Rat in a Maze.
Developed by: SANTHOSH L
Register Number:  212222100046

N = 4
 

def printSolution( sol ):
     
    for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")
 

def isSafe( maze, x, y ):
     
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
     
    return False
 

def solveMaze( maze ):
     
    # Creating a 4 * 4 2-D list
    sol = [ [ 0 for j in range(4) ] for i in range(4) ]
     
    if solveMazeUtil(maze, 0, 0, sol) == False:
        print("Solution doesn't exist");
        return False
     
    printSolution(sol)
    return True
     

def solveMazeUtil(maze, x, y, sol):
    if not isSafe(maze,x,y):
        return False
        
    if x== N-1 and y== N-1:
        sol[x][y]=1
        return True
    sol[x][y]=1
    
    if solveMazeUtil(maze,x+1,y,sol):
        return True
        
    if solveMazeUtil(maze,x,y+1,sol):
        return True
        
    sol[x][y]=0
    return False
     
# Driver program to test above function
if __name__ == "__main__":
    # Initialising the maze
    maze = [ [1, 0, 0, 0],
             [1, 1, 0, 1],
             [0, 1, 0, 0],
             [1, 1, 1, 1] ]
              
    solveMaze(maze)
```

## Output:

![Screenshot 2025-04-29 113029](https://github.com/user-attachments/assets/b439db2b-f92c-4a50-92ea-6198118521e5)


## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
