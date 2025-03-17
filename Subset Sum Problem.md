# Using Recursion

## Time Complexity : O(2^N)

```cpp []
class Solution {
  public:
    bool find(vector<int>& arr, int remaining, int idx) {
        if(remaining == 0)
        return true;
        
        if(idx >= arr.size())
        return false;
        
        bool include = false;
        if(arr[idx] <= remaining)
        include = find(arr, remaining - arr[idx], idx + 1);
        
        bool exclude = find(arr, remaining, idx + 1);
        
        return include || exclude;
    }
  
    bool isSubsetSum(vector<int>& arr, int sum) {
        // code here
        return find(arr, sum, 0);
    }
};
```

# Using DP

## Time Complexity : O(N*Sum)

```cpp []
class Solution {
  public:
    bool isSubsetSum(vector<int>& arr, int sum) {
        // code here
        vector<bool>dp(sum + 1, false);
        dp[0] = true;
        
        for(int i = 0; i < arr.size(); i++) {
            for(int j = sum; j >= arr[i]; j--) {
                if(dp[j - arr[i]])
                dp[j] = true;
            }
        }
        
        return dp[sum];
    }
};
```