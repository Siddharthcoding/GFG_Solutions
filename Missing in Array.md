# Linear search

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int missingNum(vector<int>& arr) {
        // code here
        sort(arr.begin(), arr.end());
        int j = 1;
        for(int i = 0; i < arr.size(); i++) {
            if(arr[i] != j)
            return j;
            
            j++;
        }
        
        return j;
    }
};
```

