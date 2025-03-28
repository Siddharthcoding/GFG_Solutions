# Using brute force

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int activitySelection(vector<int> &start, vector<int> &finish) {
        // code here
        int n = start.size();
        vector<pair<int, int>>act;
        
        for(int i = 0; i < n; i++) {
            act.push_back ({finish[i], start[i]});
        }
        
        sort(act.begin(), act.end());
        int maxAct = 0, lastAct = act[0].first;
        
        for(int i = 1; i < n; i++) {
            if(act[i].second > lastAct) {
                maxAct++;
                lastAct = act[i].first;
            }
        }
        
        return maxAct+1;
    }
};

```