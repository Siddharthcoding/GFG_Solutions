# Checking multiple rows having 1's at same column position

## Time Complexity : O(M*N^2)

``` cpp []
class Solution {
  public:
    bool ValidCorner(vector<vector<int> >& mat) {
        // code here
        int m = mat.size(), n = mat[0].size();
        
        unordered_set<string>st;
        
        for(int i = 0; i < m; i++) {
            vector<int>ones;
            
            for(int j = 0; j < n; j++) {
                if(mat[i][j] == 1)
                ones.push_back(j);
            }
            
            for(int p = 0; p < ones.size(); p++) {
                for(int q = p + 1; q < ones.size(); q++) {
                    string checkPair = to_string(ones[p]) + "#" + to_string(ones[q]);
                    
                    if(st.count(checkPair)) {
                        return true;
                    }
                    
                    st.insert(checkPair);
                }
            }
        } 
        
        return false;
    }
};
```

