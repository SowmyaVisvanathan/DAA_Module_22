# EX 4B DYNAMIC PROGRAMMING – 2
## DATE: 26-04-25
## AIM:
To find the longest string (or strings) that is a substring (or are substrings) of two strings.

## Algorithm
1. Initialize DP Table
   - Create a 2D array dp of size (m+1) x (n+1) where m = len(X) and n = len(Y).
   - dp[i][j] will hold the length of the longest common substring ending at X[i-1] and Y[j-1].
2. Track Max Length and End Position
   - max_len: stores the length of the longest common substring found so far.
   - end_pos: stores the end index of this substring in string X.
3. Fill DP Table
   - Loop through both strings:
     - If X[i] == Y[j]: extend the substring → dp[i+1][j+1] = dp[i][j] + 1
     - Update max_len and end_pos if new longer substring is found.
     - If not equal → reset dp[i+1][j+1] = 0 (substrings must be contiguous)
4. Extract Result
   - Substring of X from end_pos - max_len to end_pos is the answer.
## Program:
```
/*
Program to implement the longest common substring problem
Developed by: Sowmya V
Register Number: 212222110045
*/
def longest_common_substring(X, Y):
    m, n = len(X), len(Y)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    max_len = 0
    end_pos = 0

    for i in range(m):
        for j in range(n):
            if X[i] == Y[j]:
                dp[i+1][j+1] = dp[i][j] + 1
                if dp[i+1][j+1] > max_len:
                    max_len = dp[i+1][j+1]
                    end_pos = i + 1  
            else:
                dp[i+1][j+1] = 0

    return X[end_pos - max_len:end_pos]

```
## Output:
![image](https://github.com/user-attachments/assets/1c7f1604-0fa2-4253-95a3-5e8c6edb0be5)

## Result:
Thus the program was executed successfully for finding the longest common substring .
