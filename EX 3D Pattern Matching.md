# EX 3D Pattern Matching
## DATE: 29.03.2025
## AIM:
To write a python program to implement pattern matching on the given string using Brute Force algorithm.

## Algorithm:

1. Define function `BF(s1, s2)` to search for substring `s2` in string `s1` using brute-force.  
2. Initialize indices `i = 0` for `s1` and `j = 0` for `s2`.  
3. Loop while both indices are within their respective string lengths.  
4. If characters `s1[i]` and `s2[j]` match, increment both `i` and `j`.  
5. If there's a mismatch, shift the comparison window in `s1` by resetting `i = i - j + 1` and `j = 0`.  
6. After the loop, if `j == len(s2)`, a match is found; return the starting index `i - len(s2)`.  
7. If no match is found, return `0`.  
8. In `main`, read two input strings `a1` and `a2`.  
9. Call the function `BF(a1, a2)` and store the result in `b`.  
10. Print the result `b` which is the index of the first match (or `0` if not found).  

## Program:
```
/*
Program to implement the Pattern Matching.
Developed by: AKSHAYAA M
Register Number: 212222230009
*/
```
```python
def BF(s1,s2):
    i=0
    j=0
    while(i<len(s1) and j<len(s2)):
        if(s1[i] == s2[j]):
            i += 1
            j += 1
        else:
            i = i- j+1
            j=0
    if(j>=len(s2)):
        return i - len(s2)
    else:
        return 0
if __name__ == "__main__":
    a1=input() 
    a2=input() 
    b=BF(a1,a2)
    print(b)
```

## Output:

![image](https://github.com/user-attachments/assets/397b0167-49a3-4706-8ea0-d399af8e3438)

## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
