# EX 4C DYNAMIC PROGRAMMING – 3
## DATE: 22-04-25
## AIM:
Given a sequence, find the length of the longest palindromic subsequence in it.

## Algorithm
1. Initialize DP Table
   - Create a 2D array dp[n][n] where n = len(X).
   - dp[i][j] stores the length of the LPS in the substring X[i..j].
2. Base Case:
   - Every single character is a palindrome of length 1. So set dp[i][i] = 1.
3. Build the DP Table
   - For all substring lengths l from 2 to n:
   - For each starting index i, compute the end index j = i + l - 1.
     - If characters match: X[i] == X[j]:
     - Extend inner palindrome: dp[i][j] = dp[i+1][j-1] + 2
     - Else:
     - Take max between skipping one char from left or right: dp[i][j] = max(dp[i+1][j], dp[i][j-1])

4. Return Final Answer
   - The length of the longest palindromic subsequence in the whole string is dp[0][n-1].

  

## Program:
```
/*
Program to implement to find the length of the longest palindromic subsequence in it
Developed by: Sowmya V
Register Number: 212222110045
*/

def Lps(X):
    n=len(X)
    dp=[[0 for _ in range(n)] for _ in range(n)]
    for x in range(n):
        dp[x][x]=1
    for l in range(2,n+1):
        for i in range(n-l+1):
            j=i+l-1
            if X[i]==X[j]:
                dp[i][j]=dp[i+1][j-1]+2
            else:
                dp[i][j]=max(dp[i+1][j],dp[i][j-1])
    return dp[0][n-1]
X=input()
print("The length of the LPS is",Lps(X))
        
```
## Output:
![image](https://github.com/user-attachments/assets/bc85368d-e125-4038-83a1-a087534d26d7)

## Result:
Thus the program was executed successfully for finding the length of longest palindromic string.
