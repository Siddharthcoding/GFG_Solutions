# Brute Force Solution (Using Recursion)

## Time Complexity : O(2^sum)

```cpp []
class Solution {
  public:
    int solve(vector<int>&coins, int n, int sum) {
        if(sum == 0)
        return 1;
        
        if(sum < 0 || n == 0)
        return 0;
        
        return solve(coins, n, sum-coins[n-1]) + solve(coins, n-1, sum);
    }
  
    int count(vector<int>& coins, int sum) {
        // code here.
        int n = coins.size();
        
        return solve(coins, n, sum);
    }
};
```

# Better Solution (Using DP)

## Time Complexity : O(N*Sum)

```cpp []
class Solution {
  public:
    int solve(vector<int>&coins, int n, int sum, vector<vector<int>>&dp) {
        if(sum == 0)
        return 1;
        
        if(sum < 0 || n == 0)
        return 0;
        
        if(dp[n][sum] != -1)
        return dp[n][sum];
        
        return dp[n][sum] = solve(coins, n, sum-coins[n-1], dp) + solve(coins, n-1, sum, dp);
    }
  
    int count(vector<int>& coins, int sum) {
        // code here.
        int n = coins.size();
        vector<vector<int>> dp(n + 1, vector<int>(sum + 1, -1));
        
        return solve(coins, n, sum, dp);
    }
};
```
