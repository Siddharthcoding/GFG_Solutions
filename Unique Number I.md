# Frequency calculation using map

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int findUnique(vector<int> &arr) {
        // code here
        unordered_map<int,int>freq;
        for(int i = 0; i < arr.size(); i++) {
            freq[arr[i]]++;
        }
        
        for(it : freq) {
            if(it.second == 1)
            return it.first;
        }
    }
};
```

# Optimised approach - Using bitwise XOR

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int findUnique(vector<int> &arr) {
        // code here
        int total = arr[0];
        for(int i = 1; i < arr.size(); i++) {
            total ^= arr[i];
        }
        
        return total;
    }
};
```

