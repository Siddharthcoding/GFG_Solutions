# Using DP with Memoization

## Time Complexity : O(N + M)

``` cpp []
class Solution {
  public:
    int countWays(int m, int n, int target, int sum, vector<vector<int>>&dp) {
        if(n == 0 && sum != target)
        return 0;
        
        if(sum == target && n == 0)
        return 1;
        
        if(dp[n][sum] != -1)
        return dp[n][sum];
        
        int count = 0;
        
        for(int i = 1; i <= m; i++) {
            if(sum + i <= target)
            count += countWays(m, n-1, target, sum + i, dp);
        }
        
        return dp[n][sum] = count;
    }
  
    int noOfWays(int m, int n, int x) {
        // code here
        vector<vector<int>>dp(n+1, vector<int>(x+1, -1));
        
        return countWays(m, n, x, 0, dp);
    }
};
```

