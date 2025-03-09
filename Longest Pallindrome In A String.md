# Brute Force Solution

## Time Complexity : O(N^3)

```cpp []
class Solution {
  public:
    bool isPallindrome(string str) {
        int i = 0, j = str.size()-1;
        while(i <= j) {
            if(str[i] != str[j])
            return false;
            
            i++;
            j--;
        }
        
        return true;
    }
  
    string longestPalindrome(string &s) {
        // code here
        int start = -1, end = 0;
        for(int i = 0; i < s.size(); i++) {
            for(int j = i; j < s.size(); j++) {
                int len = j - i + 1;
                string temp = s.substr(i, len);
                if(isPallindrome(temp) && len > end) {
                    start = i;
                    end = len;
                }
            }
        }
        
        return s.substr(start, end);
    }
};
```

# Optimised Solution(Using DP)

## Time Complexity : O(N^2)

```cpp []
class Solution {
  public:
    string longestPalindrome(string &s) {
        // code here
        int n = s.size();
    
        vector<vector<bool>> dp(n, vector<bool>(n, false));
        int start = 0, end = 1;
    
        for (int i = 0; i < n; i++) {
            dp[i][i] = true;
        }
    
        for (int i = 0; i < n - 1; i++) {
            if (s[i] == s[i + 1]) {
                dp[i][i + 1] = true;
                start = i;
                end = 2;
            }
        }
    
        for (int len = 3; len <= n; len++) {
            for (int i = 0; i <= n - len; i++) {
                int j = i + len - 1; 
                if (s[i] == s[j] && dp[i + 1][j - 1]) {
                    dp[i][j] = true;
                    if (len > end) { 
                        start = i;
                        end = len;
                    }
                }
            }
        }
    
        return s.substr(start, end);
    }
};
```