# Using BFS

## Time Complexity : O(2^N)

``` cpp []
class Solution {
  public:
    vector<int> topoSort(int V, vector<vector<int>>& edges) {
        // code here
        vector<vector<int>>adj(V);
        for(int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
        }
        
        vector<int>InDeg(adj.size(), 0);
        queue<int>q;
        
        for(int i = 0; i < adj.size(); i++)
        for(int j = 0; j < adj[i].size(); j++)
        InDeg[adj[i][j]]++;
        
        for(int i = 0; i < InDeg.size(); i++)
        if(!InDeg[i])
        q.push(i);
        
        vector<int>ans;
        
        while(!q.empty()) {
            int node = q.front();
            q.pop();
            ans.push_back(node);
            
            for(int j = 0; j < adj[node].size(); j++) {
                InDeg[adj[node][j]]--;
                if(!InDeg[adj[node][j]])
                q.push(adj[node][j]);
            }
        }
        
        return ans;
    }
};
```

