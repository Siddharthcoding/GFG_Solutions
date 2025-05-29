# Using DFS to find the longest path in the tree with its sum

## Time Complexity : O(V+E)

``` cpp []
class Solution {
  public:
    // Helper function to find sum and length
    void findSum(Node* root, int currSum, int currLen, int& maxLen, int& maxSum) {
        if (!root) 
        return;

        currSum += root->data;
        currLen++;

        if (!root->left && !root->right) {
            if (currLen > maxLen) {
                maxLen = currLen;
                maxSum = currSum;
            } else if (currLen == maxLen) {
                maxSum = max(maxSum, currSum);
            }
            return;
        }

        findSum(root->left, currSum, currLen, maxLen, maxSum);
        findSum(root->right, currSum, currLen, maxLen, maxSum);
    }

    int sumOfLongRootToLeafPath(Node *root) {
        int maxLen = 0, maxSum = 0;
        
        findSum(root, 0, 0, maxLen, maxSum);
        return maxSum;
    }
};
```

