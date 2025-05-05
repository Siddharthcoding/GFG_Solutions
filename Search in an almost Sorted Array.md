# Using modified binary search

## Time Complexity : O(LogN)

``` cpp []
class Solution {
  public:
    int findTarget(vector<int>& arr, int target) {
        // code here
        int low = 0, high = arr.size()-1;
        while(low <= high) {
            int mid = (low + high) / 2;
            
            if(arr[mid] == target)
            return mid;
            if(mid < high && arr[mid+1] == target)
            return mid + 1;
            if(mid > low && arr[mid-1] == target)
            return mid - 1;
            
            if(arr[mid] < target)
                low = mid + 1;
            else
                high = mid - 1;
        }
        
        return -1;
    }
};
```

