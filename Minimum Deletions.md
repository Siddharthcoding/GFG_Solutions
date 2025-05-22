# Using DP with Memoization

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int longestPallindrome(string &s, int start, int end, vector<vector<int>>&dp) {
        if(start > end)
        return 0;
        
        if(start == end)
        return 1;
        
        if(dp[start][end] != -1)
        return dp[start][end];
        
        if(s[start] == s[end])
        return dp[start][end] = 2 + longestPallindrome(s, start+1, end-1, dp);
        else
        return dp[start][end] = max(longestPallindrome(s, start+1, end, dp), 
                                    longestPallindrome(s, start, end-1, dp));
    }
  
    int minDeletions(string s) {
        // code here
        int n = s.size();
        vector<vector<int>>dp(n+1, vector<int>(n+1, -1));
        
        return n - longestPallindrome(s, 0, n, dp);
    }
};
```

