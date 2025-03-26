# Using BFS

## Time Complexity : O(N^2)

``` cpp []
class Solution {
  public:
    bool wordBreak(string &s, vector<string> &dictionary) {
        // code here
        int n = s.length();
        unordered_set<string>words(dictionary.begin(), dictionary.end());
        vector<bool>visited(n+1, false);
        queue<int>q;
        
        q.push(0);
        
        while(!q.empty()) {
            int start = q.front();
            q.pop();
            
            if(start == n)
            return true;
            
            if(visited[start])
            continue;
            
            visited[start] = true;
            
            for(int end = start + 1; end <= n; end++) {
                if(words.find(s.substr(start, end-start)) != words.end()) {
                    q.push(end);
                }
            }
        }
        
        return false;
        
    }
};
```

# Using DP

## Time Complexity : O(N^2)

``` cpp []
class Solution {
  public:
    bool wordBreak(string &s, vector<string> &dictionary) {
        // code here
        int n = s.length();
        unordered_set<string>words(dictionary.begin(), dictionary.end());
        vector<bool>dp(n+1, false);
        
        dp[0] = true;
        
        for(int i = 1; i <= n; i++) {
            for(int j = 0; j < i; j++) {
                if(dp[j] && words.find(s.substr(j, i-j)) != words.end()) {
                    dp[i] = true;
                    break;
                }
            }
        }
        
        return dp[n];
    }
};
```

# Using DP with memoization

## Time Complexity : O(N^2)

``` cpp []
class Solution {
  public:
    bool solve(string &s, set<string>&words, vector<int>&dp, int index) {
        if(index == s.size())
        return 1;
        
        if(dp[index] != -1)
        return dp[index];
        
        string temp = "";
        for(int i = index; i < s.size(); i++) {
            temp += s[i];
            if(words.find(temp) != words.end()) {
                if(solve(s, words, dp, i+1))
                    return dp[index] = 1;
            }
        }
        
        return dp[index] = 0;
    }
  
    bool wordBreak(string &s, vector<string> &dictionary) {
        // code here
        int n = s.length();
        set<string>words(dictionary.begin(), dictionary.end());
        vector<int>dp(n+1, -1);
        
        return solve(s, words, dp, 0);
        
    }
};
```