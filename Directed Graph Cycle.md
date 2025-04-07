# Using Topological Sort

## Time Complexity : O(V+E)

``` cpp []
class Solution {
  public:
    bool isCyclic(int V, vector<vector<int>> &edges) {
        // code here
        vector<vector<int>>adj(V);
        for(int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
        }
        
        vector<int>InDeg(V, 0);
        
        for(int i = 0; i < V; i++)
        for(int j = 0; j < adj[i].size(); j++)
        InDeg[adj[i][j]]++;
    
        queue<int>q;
        for(int i = 0; i < V; i++)
        if(!InDeg[i])
        q.push(i);
    
        int count = 0;
    
        while(!q.empty()) {
            int node = q.front();
            q.pop();
            count++;
            
            for(int j = 0; j < adj[node].size(); j++) {
                InDeg[adj[node][j]]--;
                if(!InDeg[adj[node][j]])
                q.push(adj[node][j]);
            }
        }
        
        return count != V;
    }
};
```

