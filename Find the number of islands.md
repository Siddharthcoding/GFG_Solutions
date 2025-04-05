# Using DFS

## Time Complexity : O(N*M)

``` cpp []
class Solution {
  public:
    int dx[8]={0,1,1,1,0,-1,-1,-1}, dy[8]={1,1,0,-1,-1,-1,0,1};
    
    void helper(int i, int j, vector<vector<char>>&grid){
        if(i<0 || j<0 || i>=grid.size() || j>=grid[0].size() || grid[i][j] == 'W' || grid[i][j] == 'W'){
            return;
        }
        
        grid[i][j] = 'W';
        for(int k = 0; k < 8; k++){
            helper(i + dx[k], j + dy[k], grid);
        }
    }
    
    // Function to find the number of islands.
    int countIslands(vector<vector<char>>& grid) {
        // Code here
        int count = 0;
        for(int i = 0;i < grid.size(); i++){
            for(int j = 0;j < grid[0].size(); j++){
                if(grid[i][j] == 'L'){
                    helper(i,j,grid);
                    count++;
                }
            }
        }
        
        return count;
    }
};
```

