# Using Recursion

## Time Complexity : O(V+E)

``` cpp []
class Solution {
  public:
    void dfs(int node, vector<vector<int>>& adj, vector<int>&ans, unordered_map<int, bool>&visited) {
        visited[node] = true;
        ans.push_back(node);
        
        for(int i = 0; i < adj[node].size(); i++) {
            if(!visited[adj[node][i]])
                dfs(adj[node][i], adj, ans, visited);
        }
    }
  
    vector<int> dfs(vector<vector<int>>& adj) {
        // Code here
        unordered_map<int, bool>visited;
        vector<int>ans;
        dfs(0, adj, ans, visited);
        
        return ans;
    }
};
```

