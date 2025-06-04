# Using Dp + Memoization

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int lcs(string& s1, string& s2, string& s3, int l1, int l2, int l3, vector<vector<vector<int>>> &dp) {
        if (l1 == 0 || l2 == 0 || l3 == 0) 
            return 0;

        if (dp[l1][l2][l3] != -1) 
            return dp[l1][l2][l3];

        if (s1[l1-1] == s2[l2-1] && s2[l2-1] == s3[l3-1]) {
            return dp[l1][l2][l3] = 1 + lcs(s1, s2, s3, l1-1, l2-1, l3-1, dp);
        }

        return dp[l1][l2][l3] = max({
            lcs(s1, s2, s3, l1-1, l2, l3, dp),
            lcs(s1, s2, s3, l1, l2-1, l3, dp),
            lcs(s1, s2, s3, l1, l2, l3-1, dp)
        });
    }

    int lcsOf3(string& s1, string& s2, string& s3) {
        int l1 = s1.size(), l2 = s2.size(), l3 = s3.size();

        vector<vector<vector<int>>> dp(l1+1, vector<vector<int>>(l2+1, vector<int>(l3+1, -1)));

        return lcs(s1, s2, s3, l1, l2, l3, dp);
    }
};
```