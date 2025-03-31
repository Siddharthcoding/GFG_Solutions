# Storing last occurence of characters

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int maxPartitions(string &s) {
        // code here
        vector<int>last(26, -1);
        for(int i = 0; i < s.size(); i++) {
            last[s[i] - 'a'] = i;
        }
        
        vector<int>partitions;
        int i = 0;
        
        while(i < s.size()) {
            int pos = last[s[i] - 'a'];
            int j = i;
            
            while(j < pos) {
                pos = max(pos, last[s[j] - 'a']);
                j++;
            }
            
            partitions.push_back(j - i + 1);
            i = j + 1;
        }
        
        return partitions.size();
    }
};
```

