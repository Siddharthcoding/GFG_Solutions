# Using Greedy Approach

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int startStation(vector<int> &gas, vector<int> &cost) {
        // Your code here
        int totalGas = 0, totalCost = 0;
        for(int i = 0; i < gas.size(); i++) {
            totalGas += gas[i];
            totalCost += cost[i];
        }
        
        if(totalGas < totalCost)
        return -1;
        
        int tank = 0, index = 0;
        
        for(int i = 0; i < gas.size(); i++) {
            tank += gas[i] - cost[i];
            
            if(tank < 0) {
                index = i+1;
                tank = 0;
            }
        }
        
        return index;
    }
};
```
