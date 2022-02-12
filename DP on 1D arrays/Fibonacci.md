#### Recursion
```
def fibRec(n):
    if n == 0 or n == 1:
        return n
    return fibRec(n-1) + fibRec(n-2)

print(fibRec(7))
```

#### Memoization
```
def fibMemo(n,dp):
    if n == 0 or n == 1:
        return n
    if dp[n-1] == -1:
        ans1 = fibMemo(n-1,dp)
        dp[n-1] = ans1
    else:
        ans1 = dp[n-1]

    if dp[n-2] == -1:
        ans2 = fibMemo(n-2,dp)
        dp[n-2] = ans2
    else:
        ans2 = dp[n-2]
    ans = ans1 + ans2
    return ans

n = 7
dp = [-1 for i in range(n+1)]
print(fibMemo(n,dp))
```

#### Iterative
```
def fibIteravtive(n):
    dp = [-1 for _ in range(n+1)]
    dp[0] = 0
    dp[1] = 1
    i = 2
    while i <= n:
        dp[i] = dp[i-1] + dp[i-2]
        i += 1
    return dp[n]

print(fibIteravtive(5))
```

#### Iterative + Space Optimization
```
def fib(N): #todo no dp array required
    dp_0,dp_1 = 0,1
    for i in range(N):
        dp_0,dp_1 = dp_1,dp_1+dp_0
    return dp_0
```    
