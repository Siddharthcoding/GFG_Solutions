# Using Binary Search

## Time Complexity : O(M* log(MN))

``` cpp []
class Solution {
  public:
    int count(int mid, int m, int n) {
        int cnt = 0;
        
        for(int i = 1; i <= m; i++) {
            cnt += min(mid/i, n);
        }
        
        return cnt;
    }
  
  
    int kthSmallest(int m, int n, int k) {
        // code here
        int low = 1, high = m*n;
        
        while(low <= high) {
            int mid = (low + high) / 2;
            
            int lessEqual = count(mid, m, n);
            if(lessEqual >= k)
                high = mid - 1;
            else
                low = mid + 1;
        }
        
        return low;
        
    }
};
```

