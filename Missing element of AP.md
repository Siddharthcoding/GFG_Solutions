# By checking each element of array with actual element of AP series

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int findMissing(vector<int> &arr) {
        // code here
        int n = arr.size();
        int diff = arr[1] - arr[0];
        
        int curr = arr[0];
        for(int i = 1; i < n; i++){
            if(arr[i] != curr+diff)
            return curr+diff;
            
            curr += diff;
        }
        
        return curr + diff;
    }
};
```

