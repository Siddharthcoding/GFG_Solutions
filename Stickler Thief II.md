# Using DP

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int rob(vector<int>arr) {
        int prev1 = 0, prev2 = 0;
        for(int i = 0; i < arr.size(); i++) {
            int curr = max(prev1, prev2 + arr[i]);
            prev2 = prev1;
            prev1 = curr;
        }
        
        return prev1;
    }
  
    int maxValue(vector<int>& arr) {
        // your code here
        if(arr.size() == 1)
        return arr[0];
        
        vector<int>skipFirst(arr.begin()+1, arr.end());
        vector<int>skipLast(arr.begin(), arr.end()-1);
        
        return max(rob(skipFirst), rob(skipLast));
    }
};
```

