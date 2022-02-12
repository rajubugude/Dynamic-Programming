#### here in question if they gave, array elements includes "0"

![20220212_131213](https://user-images.githubusercontent.com/88735632/153702350-f2c74e2b-eaec-428a-a5c0-77d8d0972e1d.jpg)

```
def helper(arr,s,n,dp):
    if n == 0:
        if s == 0 and arr[0] == 0:
            return 2
        if s == 0 or arr[0] == s:
            return 1
        else:
            return 0

    if dp[n][s] != -1:
        return dp[n][s]

    notaken = helper(arr,s,n-1,dp)
    taken = 0
    if arr[n] <= s:
        taken = helper(arr,s-arr[n],n-1,dp)
    dp[n][s] = taken + notaken
    return dp[n][s]


def findWays(arr,s):
    # Write your code here.
    N = len(arr)
    dp = [[-1 for _ in range(s+1)] for _ in range(N)]
    return helper(arr,s,N-1,dp)  
```
