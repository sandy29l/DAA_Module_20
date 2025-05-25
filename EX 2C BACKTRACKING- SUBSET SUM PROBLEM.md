# EX 2C BACKTRACKING- SUBSET SUM PROBLEM
## DATE:11.03.2025
## AIM:
To demonstrate that the sum of the subset of a given set is equal to the given sum.

## Algorithm:
```
1.Input the size of the array size
2.Input size number of elements into list a
3.Input the target sum value
4.Define a recursive function SubsetSum(a, i, sum, target, n)
 • If i == n (end of list):
  – Return True if sum == target
  – Else return False
 • If sum > target:
  – Return False
 • If sum == target:
  – Return True
 • Else:
  – Return the result of either:
   • Not including current element: SubsetSum(a, i + 1, sum, target, n)
• Including current element: SubsetSum(a, i + 1, sum + a[i], target, n)
5.Call the function with initial values:
 SubsetSum(a, 0, 0, target, n)
6. If result is True:
 • Print elements of the array
 • Print "True, subset found"
7.Else:
 • Print elements of the array
 • Print "False, subset not found"
```

## Program:
```

Program to implement Subset sum problem.
Developed by: SANTHOSH L
Register Number:  212222100046

def SubsetSum(a,i,sum,target,n):
    if i==n:
        return sum==target
    if sum>target:
        return False
    if sum==target:
        return True
    return SubsetSum(a,i+1,sum,target,n) or SubsetSum(a,i+1,sum+a[i],target,n)
a=[]
size=int(input())
for i in range(size):
    x=int(input())
    a.append(x)

target=int(input())
n=len(a)
if(SubsetSum(a,0,0,target,n)==True):
    for i in range(size):
        print(a[i])
    print("True,subset found")
else:
    for i in range(size):
        print(a[i])
    print("False,subset not found")


```

## Output:
![Screenshot 2025-04-29 113951](https://github.com/user-attachments/assets/a66cd300-41d7-48e8-9015-f337970d4815)



## Result:
The Subset Sum program executed successfully, and the result was determined based on whether a subset matching the target sum was found or not.
