# Using BFS

## Time Complexity : O(V+E)

``` cpp []
class Solution {
  public:
    bool BFS(int node, vector<vector<int>>&adj, vector<bool>&visited) {
        visited[node] = true;
        queue<pair<int, int>>q;
        q.push(make_pair(node, -1));
        
        while(!q.empty()) {
            int curr = q.front().first;
            int parent = q.front().second;
            q.pop();
            
            for(int i= 0; i < adj[curr].size(); i++) {
                if(parent == adj[curr][i])
                continue;
                
                if(visited[adj[curr][i]])
                return 1;
                
                visited[adj[curr][i]] = 1;
                q.push(make_pair(adj[curr][i], curr));
            }
            
            
        }
        
        return 0;
    }
    
    bool isCycle(int V, vector<vector<int>>& edges) {
        // Code here
        vector<vector<int>>adj(V);
        
        for(int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
            adj[edges[i][1]].push_back(edges[i][0]);
        }
        
        vector<bool>visited(V, false);
        
        for(int i = 0; i < V; i++) {
            if(!visited[i] && BFS(i, adj, visited))
            return 1;
        }
        
        return 0;
    }
};
```

