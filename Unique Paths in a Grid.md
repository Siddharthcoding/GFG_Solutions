# By recursive dp + memoization

## Time Complexity : O(N*N)

``` cpp []
class Solution {
  public:
    int dfs(vector<vector<int>>& grid, int r, int c, int n, int m, vector<vector<int>>& dp) {
        if (r >= n || c >= m || grid[r][c] == 1)
            return 0;
            
        if (r == n-1 && c == m-1)
            return 1;
            
        if (dp[r][c] != -1)
            return dp[r][c];
    
        return dp[r][c] = dfs(grid, r + 1, c, n, m, dp) + dfs(grid, r, c + 1, n, m, dp);
    }
    
    int uniquePaths(vector<vector<int>>& grid) {
        int n = grid.size(), m = grid[0].size();
        
        if (grid[0][0] == 1 || grid[n-1][m-1] == 1)
            return 0;
    
        vector<vector<int>>dp(n, vector<int>(m, -1));
        
        return dfs(grid, 0, 0, n, m, dp);
    }

};
```