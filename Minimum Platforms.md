# Using two pointer

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    // Function to find the minimum number of platforms required at the
    // railway station such that no train waits.
    int findPlatform(vector<int>& arr, vector<int>& dep) {
        // Your code here
        int n = arr.size();
        
        sort(arr.begin(), arr.end());
        sort(dep.begin(), dep.end());
        
        int platform = 0, maxPlatform = 0, i = 0, j = 0;
        
        while(i < n && j < n) {
            if(arr[i] <= dep[j]) {
                platform++;
                i++;
            } else {
                platform--;
                j++;
            }
            
            maxPlatform = max(maxPlatform, platform);
        }
        
        return maxPlatform;
    }
};
```