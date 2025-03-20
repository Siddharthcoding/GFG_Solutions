# Using Recursive DP Approach

## Time Complexity : O(2*N)

``` cpp []
class Solution {
  public:
    int solve(vector<int>& prices, int k, bool canBuy, int idx, vector<vector<vector<int>>>&dp) {
        if(idx == prices.size() || k == 0)
        return 0;
        
        if(dp[idx][k][canBuy] != -1)
        return dp[idx][k][canBuy];
        
        int take = 0, skip = 0;
        if(canBuy) {
            take = -prices[idx] + solve(prices, k, false, idx+1, dp);
            skip = solve(prices, k, true, idx+1, dp);
        } else {
            take = prices[idx] + solve(prices, k-1, true, idx+1, dp);
            skip = solve(prices, k, false, idx+1, dp);
        }
        
        return dp[idx][k][canBuy] = max(take, skip);
    }
  
    int maxProfit(vector<int> &prices) {
        // code here
        int n = prices.size();
        vector<vector<vector<int>>>dp(n, vector<vector<int>>(2+1, vector<int>(2, -1)));
        return solve(prices, 2, true, 0, dp);
    }
};
```

