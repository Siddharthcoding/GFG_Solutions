# Using Recursion and Backtracking

## Time Complexity : O(N*N)

``` cpp []
class Solution {
public:
    string maxStr;

    void findMax(string &s, int k, int idx) {
        if (k == 0 || idx == s.size()) 
        return;

        int n = s.size();
        char maxChar = s[idx];

        for (int i = idx + 1; i < n; i++) {
            if (s[i] > maxChar) {
                maxChar = s[i];
            }
        }

        if (maxChar == s[idx]) {
            findMax(s, k, idx + 1);
            return;
        }

        for (int i = idx + 1; i < n; i++) {
            if (s[i] == maxChar) {
                swap(s[i], s[idx]);
                
                if (s > maxStr) 
                maxStr = s;

                findMax(s, k - 1, idx + 1);
                swap(s[i], s[idx]); 
            }
        }
    }

    string findMaximumNum(string s, int k) {
        maxStr = s;
        findMax(s, k, 0);
        
        return maxStr;
    }
};
```

