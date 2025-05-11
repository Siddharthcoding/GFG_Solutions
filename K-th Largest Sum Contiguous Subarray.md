# Using Min Heap

## Time Complexity : O(N^2 * logK)

``` cpp []
class Solution {
  public:
    int kthLargest(vector<int> &arr, int k) {
        // code here
        priority_queue<int, vector<int>, greater<int>>sums;
        int n = arr.size();
        
        for(int i = 0; i < n; i++) {
            int sum = 0;
            for(int j = i; j < n; j++) {
                sum += arr[j];
                
                if(sums.size() < k) {
                    sums.push(sum);
                } else if(sum > sums.top()) {
                    sums.pop();
                    sums.push(sum);
                }
                
            }
            
        }

        return sums.top();
    }
};
```

