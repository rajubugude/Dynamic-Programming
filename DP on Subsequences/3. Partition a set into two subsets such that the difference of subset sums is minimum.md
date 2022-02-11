### [Problem Link Here](https://www.codingninjas.com/codestudio/problems/partition-a-set-into-two-subsets-such-that-the-difference-of-subset-sums-is-minimum_842494)

#### Hint : Use logic from SubsetSum = k and Equal subset sum partiton
i.e, subset with 0 sum and rangee = (sum(arr)), now check sum of subsets in this rangee and give minimum as output
```
import sys
def subset(N,arr,s): #top_down
    dp = [[False for _ in range(s+1)] for _ in range(N+1)]
    for i in range(N+1):
        dp[i][0] = True
                
    for i in range(1,N+1):
        for j in range(1,s+1):
            if arr[i-1] <= j:
                dp[i][j] = dp[i-1][j-arr[i-1]] or dp[i-1][j]
            else:
                dp[i][j] = dp[i-1][j]
    return dp[N]


def minSubsetSumDifference(arr, n):
    rangee = sum(arr)
    lastrow = subset(n,arr,rangee)            
    diff = sys.maxsize
    for j in range(rangee // 2, -1, -1):
        if lastrow[j] == True:
            diff = rangee - (2 * j)
            break
    return diff
```    
