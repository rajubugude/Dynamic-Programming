### [Problem Link Here](https://practice.geeksforgeeks.org/problems/0-1-knapsack-problem0945/1)

#### 1. Recursive Approach
```
def knapSackRec(W,wt,value,n):
    if n == 0:
        return 0
    if W >= wt[n-1]:
        a1 = value[n-1] + knapSackRec(W-wt[n-1],wt,value,n-1)
        a2 = knapSackRec(W,wt,value,n-1)
        ans = max(a1,a2)
        return ans
    else:
        return knapSackRec(W,wt,value,n-1)
```

#### 2.Memoization
```
def knapsackMemo(wt,val,W,n,t):
    if n == 0 or W == 0:
        return 0
    if t[n][W] != 0:
        return t[n][W]

    if wt[n-1] <= W:
        t[n][W] = max(val[n-1] + knapsackMemo(wt, val, W-wt[n-1], n-1,t),  knapsackMemo(wt, val, W, n-1,t))
        return t[n][W]
    else:
        t[n][W] = knapsackMemo(wt, val, W, n-1,t)
        return t[n][W]
```

#### 3. Iterative Approach
```
class Solution:
    def knapSack(self,W, wt, val, n):
        # code here
        dp = [[0 for _ in range(W+1)] for _ in range(n+1)]
        for i in range(n-1,-1,-1):
            for j in range(W+1):
                if j >= wt[i]:
                    a1 = val[i] + dp[i+1][j-wt[i]]
                    a2 = dp[i+1][j]
                    ans = max(a1,a2)
                else:
                    ans = dp[i+1][j]
                dp[i][j] = ans
        return dp[0][W]
```
