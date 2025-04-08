# Using DFS

## Time Complexity : O(N^2)

``` cpp []
class Solution {
  public:
    void dfs(int node, vector<int>adj[], vector<int>&visited, int c, int d) {
        visited[node] = true;
        for(auto it: adj[node]) {
            if(!visited[it] && !(node == c && it == d)) {
                dfs(it, adj, visited, c, d);
            }
        }
    }
  
    bool isBridge(int V, vector<vector<int>> &edges, int c, int d) {
        // Code here
        vector<int>adj[V];
        for(int i = 0; i < edges.size(); i++) {
            int u = edges[i][0];
            int v = edges[i][1];
            
            adj[u].push_back(v);
            adj[v].push_back(u);
        }
        
        vector<int>visited(V, 0);
        dfs(c, adj, visited, c, d);
        
        if(visited[d])
        return false;
        else
        return true;
    }
};
```

