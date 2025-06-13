# Using binary search

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int findTime(vector<int>arr, int s) {
        int time = 0;
        
        for(int i = 0; i < arr.size(); i++) {
            time += ceil(arr[i] / (double)s);
        }
        
        return time;
    }
  
    int kokoEat(vector<int>& arr, int k) {
        // Code here
        int n = arr.size();
        int i = 1, j = *max_element(arr.begin(), arr.end());
        
        int ans = j;
        
        while(i <= j) {
            int mid = i + (j-i) / 2;
            
            if(findTime(arr, mid) > k) {
                i = mid + 1;
            } else {
                ans = min(ans, mid);
                j = mid - 1;
            }
        }
        
        return ans;
    }
};
```