# Using Prefix Sum + Defference Array to find longest subarray with sum 0

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int longestCommonSum(vector<int> &a1, vector<int> &a2) {
        // Code here.
        unordered_map<int, int>mp;
        
        for(int i = 0; i < a1.size(); i++) {
            a1[i] -= a2[i];
        }
        
        int sum = 0, ans = 0;
        for(int i = 0; i < a1.size(); i++) {
            sum += a1[i];
            
            if(sum == 0)
            ans = i+1;
            
            if(mp.find(sum) != mp.end()) {
                ans = max(ans, i - mp[sum]);
            } else {
                mp[sum] = i;
            }
        }
        
        return ans;
    }
};
```