# Using Recursion

## Time Complexity : O(2^N)

``` cpp []
class Solution {
  public:
    int find(string &digits, int n, int i) {
        if(i == n)
        return 1;
        
        if(digits[i] == '0')
        return 0;
        
        int includeOne = find(digits, n, i + 1);
        
        int includeTwo = 0;
        if(i != n-1 && (digits[i] == '1' || digits[i] == '2' && digits[i+1] <= '6'))
        includeTwo = find(digits, n, i+2);
        
        return includeOne + includeTwo;
        
    }
  
    int countWays(string &digits) {
        // Code here
        int n = digits.size();
        return find(digits, n, 0);
    }
};
```

# Using Recursive DP

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int find(string &digits, vector<int>&dp, int n, int i) {
        if(i == n)
        return 1;
        
        if(digits[i] == '0')
        return 0;
        
        if(dp[i] != -1)
        return dp[i];
        
        int includeOne = find(digits, dp, n, i + 1);
        
        int includeTwo = 0;
        if(i != n-1 && (digits[i] == '1' || digits[i] == '2' && digits[i+1] <= '6'))
        includeTwo = find(digits, dp, n, i + 2);
        
        return dp[i] = includeOne + includeTwo;
        
    }
  
    int countWays(string &digits) {
        // Code here
        int n = digits.size();
        vector<int>dp(n+1, -1);
        
        return find(digits, dp, n, 0);
    }
};
```

