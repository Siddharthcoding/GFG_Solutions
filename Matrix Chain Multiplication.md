# Using DP

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int find(vector<int>&arr, int start, int end, vector<vector<int>>&dp) {
        if(end - start == 1) 
        return 0;
        
        if(dp[start][end] != -1)
        return dp[start][end];
        
        int ans = INT_MAX;
        for(int i  = start+1; i < end; i++) {
            int left = find(arr, start, i, dp);
            int right = find(arr, i, end, dp);
            
            ans = min(ans, left + right + arr[start]*arr[end]*arr[i]);
        }
        
        return dp[start][end] = ans;
    }
  
    int matrixMultiplication(vector<int> &arr) {
        // code here
        int n = arr.size();
        vector<vector<int>>dp(n, vector<int>(n, -1));
        return find(arr, 0, n-1, dp);
        
    }
};
```