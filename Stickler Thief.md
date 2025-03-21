# Using DP

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int findMaxSum(vector<int>& arr) {
        // code here
        
        int n = arr.size();
        if(n == 1)
        return arr[0];
        
        int prev1 = arr[0], prev2 = 0;
        for(int i = 1; i < n; i++) {
            int curr = max(prev1, prev2 + arr[i]);
            prev2 = prev1;
            prev1 = curr;
        }
        
        return prev1;
    }
};
```

