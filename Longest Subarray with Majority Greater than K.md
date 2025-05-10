# Using Hashmap for prefix sum with difference counter

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int longestSubarray(vector<int> &arr, int k) {
        // Code here
        int n = arr.size();
        int ans = 0, moreCount = 0;
        unordered_map<int, int>mp;
        mp[0] = -1;
        
        for(int r = 0; r < n; r++) {
            if(arr[r] > k)
                moreCount++;
            else
                moreCount--;
            
            if(moreCount > 0) 
                ans = r+1;
            else {
                if(mp.find(moreCount-1) != mp.end())
                    ans = max(ans, r - mp[moreCount-1]);
                    
                if(mp.find(moreCount) == mp.end())
                    mp[moreCount] = r;
            }
        }
        
        return ans;
    }
};
```

