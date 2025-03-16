# Using Binary Search

## Time Complexity : O(N + maxRank*log(maxRank))

``` cpp []
class Solution {
  public:
    int minJumps(vector<int>& arr) {
        // code here
        int n = arr.size();
        
        if(arr[0] == 0)
        return -1;
        
        if(n <= 1)
        return 0;
        
        int jumps = 1, steps = arr[0], reachable = arr[0];
        for(int i = 1; i < n; i++) {
            if(i == n-1)
            return jumps;
            
            reachable = max(reachable, arr[i] + i);
            steps--;
            if(steps == 0) {
                jumps++;
                
                if(i >= reachable)
                return -1;
                
                steps = reachable - i;
            }
        }
        
        return -1;
    }
};```

