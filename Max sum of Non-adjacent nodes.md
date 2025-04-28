# Using DP with memoization

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    unordered_map<Node*, int> dp;
  
    int solve(Node *root) {
        if(!root)
        return 0;
        
        if(dp.find(root) != dp.end()) 
        return dp[root];
        
        int skip = solve(root->left) + solve(root->right);
        int include = root->data;
        
        if(root->left) {
            include += solve(root->left->left);
            include += solve(root->left->right);
        }
        
        if(root->right) {
            include += solve(root->right->left);
            include += solve(root->right->right);
        }
        
        return dp[root] = max(skip, include);
    }
  
    // Function to return the maximum sum of non-adjacent nodes.
    int getMaxSum(Node *root) {
        // code here
        return solve(root);
    }
};
```

