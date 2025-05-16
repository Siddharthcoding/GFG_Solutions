# Using sliding window on flattened matrix

## Time Complexity : O(N*K)

``` cpp []
class Solution {
  public:
    vector<int> findSmallestRange(vector<vector<int>>& arr) {
        // code here
        vector<pair<int, int>> merged;
        for(int i = 0; i < arr.size(); i++) {
            for(int j = 0; j < arr[i].size(); j++) {
                merged.push_back({arr[i][j], i});
            }
        }
        
        sort(merged.begin(), merged.end());
        
        unordered_map<int, int> count;
        int l = 0, minRange = INT_MAX;
        int start = 0, end = 0;
        
        for(int r = 0; r < merged.size(); r++) {
            count[merged[r].second]++;
            
            while(count.size() == arr.size()) {
                int currStart = merged[l].first;
                int currEnd = merged[r].first;
                
                if(currEnd - currStart < minRange) {
                    minRange = currEnd - currStart;
                    start = currStart;
                    end = currEnd;
                }
                
                count[merged[l].second]--;
                if(count[merged[l].second] == 0)
                count.erase(merged[l].second);
                
                l++;
            }
            
        }
        
        return {start, end};
        
    }
};
```

