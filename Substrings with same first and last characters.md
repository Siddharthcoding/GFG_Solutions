# Using character frequency count

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int countSubstring(string &s) {
        // code here
        int count = s.size();
        unordered_map<char, int>freq;
        
        for(int i = 0; i < s.size(); i++) {
            if(freq.find(s[i]) != freq.end()) 
                count += freq[s[i]];
                
            freq[s[i]]++;
        }
        
        return count;
    }
};
```

