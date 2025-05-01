# Using brute force approach to calculate the nthrow iteratively

## Time Complexity : O(N^2)

``` cpp []
class Solution {
  public:
    vector<int> nthRowOfPascalTriangle(int n) {
        // code here
        vector<int>ans = {1};
        vector<int>temp;
        
        for(int i = 0; i < n-1; i++) {
            int m = ans.size();
            temp.push_back(ans[0]);
            
            for(int j = 0; j < m-1; j++) {
                temp.push_back(ans[j] + ans[j+1]);
            }
            
            temp.push_back(ans[m-1]);
            ans = temp;
            temp.clear();
        }
        
        return ans;
    }
};
```

