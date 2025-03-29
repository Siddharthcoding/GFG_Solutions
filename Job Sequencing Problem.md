# Using Greedy Approach

## Time Complexity : O(N logN)

``` cpp []
class Solution {
  public:
    vector<int> jobSequencing(vector<int> &deadline, vector<int> &profit) {
        // code here
        int n = deadline.size();
        vector<pair<int, int>>job;
        
        for(int i = 0; i < n; i++) {
            job.push_back({profit[i], deadline[i]});
        }
        
        sort(job.rbegin(), job.rend());
        
        int maxDeadline = 0;
        for(int i = 0; i < n; i++) {
            maxDeadline = max(maxDeadline, deadline[i]);
        }
        
        vector<int>slot(maxDeadline+1, -1);
        int maxProfit = 0, count = 0;
        
        for(auto j : job) {
            int prof = j.first , deadl = j.second;
            
            for(int i = deadl; i > 0; i--) {
                if(slot[i] == -1) {
                    slot[i] = prof;
                    maxProfit += prof;
                    count++;
                    break;
                }
            }
        }
        
        return {count, maxProfit};
    }
};

```
