# Sorting the elements based on their closeness and extracting the top k elements

## Time Complexity : O(NlogN)

``` cpp []
class Solution {
  public:
    static bool comp(pair<int, int>a, pair<int, int>b) {
        if(a.first == b.first)
        return a.second > b.second;
        
        return a.first < b.first;
    }
  
    vector<int> printKClosest(vector<int> arr, int k, int x) {
        // Code here
        vector<pair<int, int>>diff;
        for(int i = 0; i < arr.size(); i++) {
            diff.push_back({abs(x - arr[i]), arr[i]});
        }
        
        sort(diff.begin(), diff.end(), comp);
        vector<int>ans;
        
        for(auto it: diff) {
            if(it.first == 0)
            continue;
            
            if(ans.size() == k)
            break;
            
            ans.push_back(it.second);
        }
        
        return ans;
    }
};
```