# Using two pointers and property of quadratic equation

## Time Complexity : O(N)

``` cpp []
class Solution {
public:
    int findQuad(int x, int A, int B, int C) {
        return A * x * x + B * x + C;
    }

    vector<int>sortArray(vector<int> &arr, int A, int B, int C) {
        int n = arr.size();
        
        vector<int>ans(n);
        int left = 0, right = n - 1;
        int index = A >= 0 ? n - 1 : 0; 

        while (left <= right) {
            int valLeft = findQuad(arr[left], A, B, C);
            int valRight = findQuad(arr[right], A, B, C);

            if (A >= 0) {
                if (valLeft > valRight) {
                    ans[index] = valLeft;
                    index--;
                    left++;
                } else {
                    ans[index] = valRight;
                    index--;
                    right--;
                }
            } else {
                if (valLeft < valRight) {
                    ans[index] = valLeft;
                    index++;
                    left++;
                } else {
                    ans[index] = valRight;
                    index++;
                    right--;
                }
            }
        }

        return ans;
    }
};
```

