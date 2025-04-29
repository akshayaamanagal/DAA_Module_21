# EX 3B Hamiltonian Circuit Problem
## DATE: 22.03.2025
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm:

1. Define `Hamiltonian_path(adj, N)` to check for a Hamiltonian path in a graph with `N` vertices using its adjacency matrix.  
2. Initialize a 2D DP table `dp[i][mask]` where `i` is the current node and `mask` is the visited nodes bitmask.  
3. Set `dp[i][1 << i] = True` for all `i`, meaning a path starting at each node is valid.  
4. Iterate over all bitmasks `i` representing subsets of visited vertices.  
5. For each vertex `j` included in subset `i`, try to reach `j` from a previously visited vertex `k`.  
6. If `k` is in `i`, `adj[k][j] == 1`, `k != j`, and `dp[k][i ^ (1 << j)]` is `True`, then set `dp[j][i] = True`.  
7. After filling the DP table, check if there is any `dp[i][(1 << N) - 1] == True`, indicating a Hamiltonian path covering all vertices.  
8. Return `True` if such a path exists; otherwise, return `False`.  
9. Define the adjacency matrix `adj` representing the graph.  
10. Call `Hamiltonian_path(adj, N)` and print `"YES"` if a path exists or `"NO"` otherwise.  


## Program:
```
/*
Program to implement to check whether Hamiltonian path exits in the given graph.
Developed by: AKSHAYAA M
Register Number: 212222230009
*/
```
```python
def Hamiltonian_path(adj, N):
    dp = [[False for i in range(1 << N)] for j in range(N)]
    for i in range(N):
         dp[i][1 << i]=True
    for i in range(1 << N):
        for j in range(N):
            if ((i & (1 << j))!=0):
                for k in range(N):
                    if((i & (1 << k)) != 0 and
                            adj[k][j] == 1 and
                                    j != k and
                          dp[k][i ^ (1 << j)]):
                       dp[j][i]=True
                       break
    for i in range(N):
        if (dp[i][(1 << N)-1]):
            return True
    return False
adj = [ [ 0, 1, 1, 1, 0 ] ,
        [ 1, 0, 1, 0, 1 ],
        [ 1, 1, 0, 1, 1 ],
        [ 1, 0, 1, 0, 0 ] ]
 
N = len(adj)
 
if (Hamiltonian_path(adj, N)):
    print("YES")
else:
    print("NO")
```

## Output:

![image](https://github.com/user-attachments/assets/774d5f12-aef5-4030-994f-aac65715aabe)

## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
