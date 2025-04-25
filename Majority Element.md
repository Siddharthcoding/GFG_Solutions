# Frequecy count using map

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int majorityElement(vector<int>& arr) {
        // code here
        unordered_map<int, int>count;
        for(int i = 0; i < arr.size(); i++) {
            count[arr[i]]++;
        }
        
        for(auto it : count) {
            if(it.second > arr.size()/2)
            return it.first;
        }
        
        return -1;
    }
};
```

