# Using iterative approach and avoiding overflow

## Time Complexity : O(r)

``` cpp []
class Solution {
  public:
    long long nCr(int n, int r) {
        //code here
        if (r > n) 
        return 0;
        
        if (r == 0 || r == n) 
        return 1;
    
        r = min(r, n - r); 
        long long res = 1;
    
        for (int i = 1; i <= r; i++) {
            res *= (n - i + 1);
            res /= i;
        }
    
        return res;
    }
};
```

