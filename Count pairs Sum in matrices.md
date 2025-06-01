# Using Binary Search

## Time Complexity : O(N*LogN)

``` cpp []
class Solution {
  public:
    int countPairs(vector<vector<int>> &mat1, vector<vector<int>> &mat2, int x) {
        // code here
        int count = 0, n = mat1.size();
        int i = 0, j = n*n-1;
        
        while(i < n*n && j >= 0) {
            int r1 = i / n, c1 = i % n;
            int r2 = j / n, c2 = j % n;
            
            int num = mat1[r1][c1] + mat2[r2][c2];
            if(num == x) {
                count++;
                i++;
                j--;
            } else if(x < num) {
                j--;
            } else {
                i++;
            }
        }
        
        return count;
    }
};
```