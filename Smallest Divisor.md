# Using binary search

## Time Complexity : O(NlogN)

``` cpp []
class Solution {
  public:
    int findSum(vector<int>&arr, double mid) {
        int sum = 0;
        for(int i = 0; i < arr.size(); i++) {
            sum += ceil(arr[i] / mid);
        }
        
        return sum;
    }
  
    int smallestDivisor(vector<int>& arr, int k) {
        // Code here
        int i = 1, j = *max_element(arr.begin(), arr.end());
        int ans;
        while(i <= j) {
            int mid = i + (j-i)/2;
            
            if(findSum(arr, mid) > k) {
                i = mid + 1;
            } else {
                ans = mid;
                j = mid - 1;
            }
        }
        
        return ans;
    }
};
```