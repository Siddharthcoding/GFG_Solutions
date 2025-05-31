# Using Binary Search

## Time Complexity : O(N*LogN)

``` cpp []
class Solution {
  public:
    int check(vector<vector<int>> &matrix, int mid) {
        int count = 0;
        
        for(int i = 0; i < matrix.size(); i++) {
            int lessInRow = upper_bound(matrix[i].begin(), matrix[i].end(), mid) - matrix[i].begin();
            
            count += lessInRow;
        }
        
        return count;
    }
  
    int kthSmallest(vector<vector<int>> &matrix, int k) {
        // code here
        int n = matrix.size();
        int start = matrix[0][0], end = matrix[n-1][n-1];
        
        while(start < end) {
            int mid = (start + end) / 2;
            int count = check(matrix, mid);
            
            if(count < k) 
                start = mid + 1;
            else
                end = mid;
        }
        
        return start;
    }
};
```