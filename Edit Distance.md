# Using DP

## Time Complexity : O(N*M), where N & M are size of strings

```cpp []
class Solution {
  public:
    // Function to compute the edit distance between two strings
    int editDistance(string& s1, string& s2) {
        // code here
        int m = s1.length(), n = s2.length();
        
        vector<vector<int>> dp(m+1, vector<int>(n+1, 0));
        
        for(int i = 0; i <= m; i++)
            dp[i][0] = i;
        
        for(int j = 0; j <= n; j++)
            dp[0][j]=j;
            
        for(int i = 1; i <= m; i++) {
            for(int j = 1; j <= n; j++) {
                if(s1[i-1] == s2[j-1]) {
                    dp[i][j] = dp[i-1][j-1];
                } else {
                    dp[i][j] = min(min(dp[i-1][j] + 1, dp[i][j-1] + 1), dp[i-1][j-1] + 1);
                }
            }
        }
        
        return dp[m][n];
    }
};
```