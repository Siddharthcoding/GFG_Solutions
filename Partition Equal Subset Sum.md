# Using Recursive Approach

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    bool find(vector<int>& arr, int sum, int index) {
        if(sum < 0)
        return false;
        
        if(index > arr.size())
        return false;
        
        if(sum == 0)
        return true;
        
        return find(arr, sum - arr[index], index+1) || find(arr, sum, index+1);
    }
  
    bool equalPartition(vector<int>& arr) {
        // code here
        int totalSum = accumulate(arr.begin(), arr.end(), 0);
        
        if (totalSum % 2 != 0) 
            return false;

        int target = totalSum / 2;
        
        return find(arr, target, 0);
    }
};
```

