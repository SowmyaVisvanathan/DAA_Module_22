# EX 4A DYNAMIC PROGRAMMING - 1
## DATE: 15-04-25
## AIM:
To find longest common subsequence using Dynamic Programming.

## Algorithm
1. Initialize DP Table
   - Create a 2D array dp of size (m+1) x (n+1) where m = len(X) and n = len(Y).
   - dp[i][j] stores the length of LCS of X[0..i-1] and Y[0..j-1].
2. Fill DP Table
   - For each i in X and j in Y:
     - If X[i] == Y[j], increment diagonal value: dp[i+1][j+1] = dp[i][j] + 1
     - Else, take the max from top or left: dp[i+1][j+1] = max(dp[i][j+1], dp[i+1][j])
3. Backtrack to Find LCS String
   - Start from dp[m][n] and trace back:
     - If characters match, add to result and move diagonally.
     - Else, move to the direction of the greater value (up or left).
4. Return Result
   - The result is built in reverse, so reverse it at the end. 

## Program:
```
/*
Program to implement the longest common subsequence using Dynamic Programming
Developed by: Sowmya V
Register Number: 212222110045
*/

def lcs(X, Y):
    m, n = len(X), len(Y)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(m):
        for j in range(n):
            dp[i+1][j+1] = dp[i][j] + 1 if X[i] == Y[j] else max(dp[i][j+1], dp[i+1][j])
    lcs, i, j = [], m, n
    while i and j:
        if X[i-1] == Y[j-1]:
            lcs.append(X[i-1])
            i, j = i-1, j-1
        elif dp[i-1][j] > dp[i][j-1]: i -= 1
        else: j -= 1
    return "".join(lcs[::-1])

print(lcs(input(), input()))

```
## Output:
![image](https://github.com/user-attachments/assets/111d2fd1-cd84-4fb4-9c07-01bfc829992e)

## Result:
Thus the program was executed successfully for computing the length of longest common subsequence.
