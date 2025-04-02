# Using Basic Iteration 

## Time Complexity : O(V+E)

``` cpp []
class Solution {
  public:
    // Function to return Breadth First Traversal of given graph.
    vector<int> bfs(vector<vector<int>> &adj) {
        // Code here
        queue<int>q;
        q.push(0);
        
        unordered_map<int, bool>visited;
        visited[0] = true;
        
        vector<int>ans;
        while(!q.empty()) {
            int node = q.front();
            q.pop();
            
            ans.push_back(node);
            
            for(int i = 0; i < adj[node].size(); i++) {
                if(!visited[adj[node][i]]) {
                    q.push(adj[node][i]);
                    visited[adj[node][i]] = true;
                }
            }
        }
        
        return ans;
        
    }
};
```

