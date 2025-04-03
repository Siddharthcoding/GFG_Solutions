# Using BFS

## Time Complexity : O(N*M)

``` cpp []
class Solution {
  public:
    int r, c;
    int row[4] = {-1, 1, 0, 0};
    int col[4] = {0, 0, -1, 1};
    
    bool valid(int i, int j) {
        return i>= 0 && i<r && j>=0 && j<c;
    }
    
    // Function to find minimum time required to rot all oranges.
    int orangesRotting(vector<vector<int>>& mat) {
        // Code here
        r = mat.size();
        c = mat[0].size();
        queue<pair<int, int>>q;
        
        for(int i = 0; i < r; i++)
        for(int j = 0; j < c; j++)
        if(mat[i][j] == 2)
        q.push(make_pair(i, j));
        
        int timer = -1;
        
        while(!q.empty()) {
            timer++;
            int curr_rotten = q.size();
            
            while(curr_rotten--) {
                int i = q.front().first;
                int j = q.front().second;
                q.pop();
                
                for(int k = 0; k < 4; k++) {
                    if(valid(i+row[k], j+col[k]) && mat[i+row[k]][j+col[k]] == 1) {
                        mat[i+row[k]][j+col[k]] = 2;
                        q.push(make_pair(i+row[k], j+col[k]));
                    }
                }
            }
        }
        
        for(int i = 0; i < r; i++)
        for(int j = 0; j < c; j++) {
            if(mat[i][j] == 1)
            return -1;
        }
        
        return timer == -1 ? 0 : timer;
    }
};
```

