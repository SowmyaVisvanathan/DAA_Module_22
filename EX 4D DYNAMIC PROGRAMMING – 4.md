# EX 4D DYNAMIC PROGRAMMING – 4
## DATE: 26-04-25
## AIM:
To find the minimum number of operations to convert str1 to str2 using Naive recursive method.
## Algorithm
1. Base Cases:
   - If s is empty: return len(t) → all characters of t must be inserted.
   - If t is empty: return len(s) → all characters of s must be deleted.
2. Check Last Characters:
   - If s[-1] == t[-1]: no cost → cost = 0
   - Else: substitution needed → cost = 1
3. Recursive Cases (Three Possibilities):
   - Delete from s: LD(s[:-1], t) + 1
   - Insert into s: LD(s, t[:-1]) + 1
   - Substitute last character: LD(s[:-1], t[:-1]) + cost
4. Take Minimum of All Options:
   - res = min(delete, insert, substitute)
5. Return Final Result:
   - The recursive function returns the minimum edit distance.
## Program:
```
/*
Program to implement to find the minimum number of operations to convert str1 to str2 using Naive recursive method
Developed by: Sowmya V
Register Number: 212222110045
*/

def LD(s,t):
	if s=="":
		return len(t)
	if t=="":
		return len(s)
	if s[-1]==t[-1]:
		cost=0
	else:
		cost=1
	res=min([LD(s[:-1],t)+1,LD(s,t[:-1])+1,LD(s[:-1],t[:-1])+cost])
	return res
str1=input()
str2=input()
print("Edit Distance",LD(str1,str2))
```
## Output:
![image](https://github.com/user-attachments/assets/b86bdc88-9af9-4d52-8a20-a5aa90f76bb7)

## Result:
Thus the program was executed successfully for finding edit distance between two strings.
