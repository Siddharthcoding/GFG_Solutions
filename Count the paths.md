# Using dfs + memoization

## Time Complexity : O(V+E)

``` cpp []
class Solution {
  public:
    int dfs(vector<vector<int>>&adj, int curr, int dest, vector<int>&dp) {
        if(curr == dest) {
            return 1;
        }
        
        if(dp[curr] != -1)
        return dp[curr];
        
        int paths = 0;
        
        for(int neighbour: adj[curr]) {
            paths += dfs(adj, neighbour, dest, dp);
        }
        
        return dp[curr] = paths;
        
    }
  
    int countPaths(vector<vector<int>>& edges, int V, int src, int dest) {
        // Code here
        vector<vector<int>>adj(V);
        
        for(auto edge: edges) {
            adj[edge[0]].push_back(edge[1]);
        }
        
        vector<int>dp(V, -1);
        
        return dfs(adj, src, dest, dp);
    }
};
```