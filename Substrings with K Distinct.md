# By DFS

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int atMost(string &s, int k) {
        unordered_map<char, int>freq;
        int l = 0, count = 0;
        
        for(int r = 0; r < s.size(); r++) {
            freq[s[r]]++;
            
            while(freq.size() > k) {
                freq[s[l]]--;
                
                if(freq[s[l]] == 0)
                freq.erase(s[l]);
                
                l++;
            }
            
            count += r-l+1;
        }
        
        return count;
    }
  
    int countSubstr(string& s, int k) {
        // code here.
        return atMost(s, k) - atMost(s, k-1);
    }
};
```