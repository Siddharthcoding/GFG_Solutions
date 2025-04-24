# Frequency calculation using map

## Time Complexity : O(N)
## Space Complexity : O(N)

``` cpp []
class Solution {
  public:
    int getSingle(vector<int> &arr) {
        // code here
        unordered_map<int, int>freq;
        
        for(int i = 0; i < arr.size(); i++) {
            freq[arr[i]]++;
        }
        
        for(auto it: freq) {
            if(it.second == 1)
            return it.first;
        }
    }
};
```

# Optimised approach(Using bitwise operators)

## Time Complexity : O(N)
## Space Complexity : O(1)

``` cpp []
class Solution {
  public:
    int getSingle(vector<int> &arr) {
        // code here
        int ans = 0;
        for(int i = 0; i < 32; i++) {
            int bitSum = 0;
            
            for(int j = 0; j < arr.size(); j++) { // numbers having ith bit 1
                if((arr[j] >> i) & 1) {
                    bitSum++;
                }
            }
            
            if(bitSum % 3 != 0) {   // required number which doesn't appears thrice
                ans |= (1 << i);    // set the ith bit
            }
        }
        
        return ans;
    }
};
```

