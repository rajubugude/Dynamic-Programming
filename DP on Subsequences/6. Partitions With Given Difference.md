### [Problem Link Here](https://www.codingninjas.com/codestudio/problems/partitions-with-given-difference_3751628?source=youtube&campaign=striver_dp_videos&utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_dp_videos&leftPanelTab=0)

#### Memoization Code
```
mod = 10**9+7

def helper(arr,s,n,dp):
    if n == 0:
        if s == 0:
            return 1
        return 0

    if dp[n][s] != -1:
        return dp[n][s]

    notaken = helper(arr,s,n-1,dp)
    taken = 0
    if arr[n-1] <= s:
        taken =  helper(arr,s-arr[n-1],n-1,dp)
    dp[n][s] = (taken + notaken)%mod
    return dp[n][s]

def countPartitions(N: int, d: int, arr: List[int]) -> int:       
    total = 0
    for i in range(N):
        total += arr[i]
    if (total < d or (total- d) % 2):
        return 0
        
    s = (total-d)//2
    dp = [[-1 for _ in range(s+1)] for _ in range(N+1)]
    return helper(arr,s,N,dp) 
```

#### Iterative Code

```
mod = 10**9+7
def countPartitions(n: int, d: int, arr: List[int]) -> int:
    total = 0
    for i in range(n):
        total += arr[i]
    if (total < d or (total- d) % 2):
        return 0

    s = (total-d)//2
    dp = [[0 for _ in range(s+1)] for _ in range(n+1)]
    
    dp[0][0] = 1
    for i in range(1,n+1):
        for j in range(s+1):
            notaken = dp[i-1][j]
            taken = 0
            if arr[i-1] <= j:
                taken =  dp[i-1][j-arr[i-1]]
            dp[i][j] = (taken + notaken)%mod
    return dp[n][s]
```
