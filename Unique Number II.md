# Frequency calculation using map

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    vector<int> singleNum(vector<int>& arr) {
        // Code here.
        map<int, int>freq;
        for(int i = 0; i < arr.size(); i++) {
            freq[arr[i]]++;
        }
        
        vector<int>ans;
        for(auto it : freq) {
            if(it.second == 1)
            ans.push_back(it.first);
        }
        
        return ans;
    }
};
```

