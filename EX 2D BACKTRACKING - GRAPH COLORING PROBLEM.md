# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:15.03.2025
## AIM:
To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.

## Algorithm:
```
1.Input the number of vertices V in the graph
2.Initialize an adjacency matrix graph[V][V]
 • Each element graph[i][j] is 1 if there is an edge between vertex i and vertex j, otherwise 0
3.Input the maximum number of colors M available
4.Create a list colour of size V initialized to 0
 • This list will store the color assigned to each vertex
5.Define a function isSafe(vertex, colour[], c)
 • For all vertices i from 0 to V-1:
  – If graph[vertex][i] == 1 and colour[i] == c, return False
 • Return True if the color can be assigned
6.Define a recursive function graphColourUtil(m, colour[], v)
 • If v == V (all vertices processed):
  – Return True
• For every color c from 1 to m:
  – If isSafe(v, colour, c) is True:
   • Assign color c to colour[v]
   • Recur for next vertex v + 1
   • If recursion returns True, return True
   • Else, backtrack: set colour[v] = 0
 • Return False if no color can be assigned
7. Call the function graphColouring(m)
 • If solution exists, print the assigned colors
 • Else, print "Solution does not exist"
```

## Program:
```
Program to implement Graph Coloring Problem using backtracking.
Developed by: SANTHOSH L
Register Number:  212222100046
class Graph():
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[0 for column in range(vertices)]for row in range(vertices)]
 
    def isSafe(self, v, colour, c):
        for i in range(self.V):
            if self.graph[v][i] == 1 and colour[i] == c:
                return False
        return True

    def graphColourUtil(self, m, colour, v):
        if v == self.V:
            return True
        for c in range(1, m + 1):
            if self.isSafe(v, colour, c) == True:
                colour[v] = c
                if self.graphColourUtil(m, colour, v + 1) == True:
                    return True
                colour[v] = 0

    def graphColouring(self, m):
        colour = [0] * self.V
        if self.graphColourUtil(m, colour, 0) == None:
            return False
        print ("Solution exist and Following are the assigned colours:")
        for c in colour:
            print (c,end=' ')
        return True
# Driver Code
```

## Output:

![Screenshot 2025-04-29 114410](https://github.com/user-attachments/assets/0f212e79-898e-45dd-bd42-c4cfbf7f32ed)


## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
