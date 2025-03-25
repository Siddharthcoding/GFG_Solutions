# Using DP

## Time Complexity : O(N)

``` cpp []
class Solution {
public:
    long long solve(int i, int j, int isTrue, string& S, vector<vector<vector<long long>>>& dp) {
        if (i > j) 
        return 0;
        
        if (i == j) 
        return (isTrue ? (S[i] == 'T') : (S[i] == 'F'));

        if (dp[i][j][isTrue] != -1) 
        return dp[i][j][isTrue];

        long long ways = 0;
        for (int ind = i + 1; ind <= j - 1; ind += 2) {
            long long lT = solve(i, ind - 1, 1, S, dp);
            long long lF = solve(i, ind - 1, 0, S, dp);
            long long rT = solve(ind + 1, j, 1, S, dp);
            long long rF = solve(ind + 1, j, 0, S, dp);

            if (S[ind] == '&') {
                if (isTrue) 
                ways += (lT * rT);
                else 
                ways += (lT * rF + lF * rT + lF * rF);
            } 
            else if (S[ind] == '|') {
                if (isTrue) 
                ways += (lT * rT + lT * rF + lF * rT);
                else 
                ways += (lF * rF);
            } 
            else if (S[ind] == '^') {
                if (isTrue) 
                ways += (lT * rF + lF * rT);
                else 
                ways += (lT * rT + lF * rF);
            }
        }
        return dp[i][j][isTrue] = ways;
    }

    int countWays(string S) {
        int N = S.length();
        vector<vector<vector<long long>>> dp(N, vector<vector<long long>>(N, vector<long long>(2, -1)));
        return solve(0, N - 1, 1, S, dp);
    }
};
```