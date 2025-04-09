# Using DFS

## Time Complexity : O(N^2)

``` cpp []
class Solution {
public:
    void dfs(int u, const vector<vector<int>>& adj, vector<int>& disc, vector<int>& low, vector<int>& parent,
        vector<bool>& visited, vector<bool>& isAP, int& time) {
        
        visited[u] = true;
        disc[u] = low[u] = time++;
        int children = 0;

        for (int v : adj[u]) {
            if (v == parent[u]) 
            continue;

            if (!visited[v]) {
                parent[v] = u;
                children++;
                dfs(v, adj, disc, low, parent, visited, isAP, time);

                low[u] = min(low[u], low[v]);

                if (parent[u] != -1 && low[v] >= disc[u]) {
                    isAP[u] = true;
                }
            } else {
                low[u] = min(low[u], disc[v]);
            }
        }

        if (parent[u] == -1 && children > 1) {
            isAP[u] = true;
        }
    }

    vector<int> articulationPoints(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        for (auto e : edges) {
            adj[e[0]].push_back(e[1]);
            adj[e[1]].push_back(e[0]);
        }

        vector<int> disc(V, -1), low(V, -1), parent(V, -1);
        vector<bool> visited(V, false), isAP(V, false);
        int time = 0;

        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                dfs(i, adj, disc, low, parent, visited, isAP, time);
            }
        }

        vector<int> result;
        for (int i = 0; i < V; i++) {
            if (isAP[i]) 
            result.push_back(i);
        }

        return result.empty() ? vector<int>{-1} : result;
    }
};
```

