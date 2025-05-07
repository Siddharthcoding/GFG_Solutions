# Using Preorder Traversal

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    void solve(Node *root, vector<vector<int>>&ans, vector<int>&currPath) {
        if(!root)
        return;
        
        if(!root->left && !root->right) {
            currPath.push_back(root->data);
            ans.push_back(currPath);
            currPath.pop_back();
            return;
        }
        
        currPath.push_back(root->data);
        solve(root->left, ans, currPath);
        solve(root->right, ans, currPath);
        
        currPath.pop_back();
    }
  
    vector<vector<int>> Paths(Node* root) {
        // code here
        vector<vector<int>>ans;
        vector<int>currPath;
        
        solve(root, ans, currPath);
        return ans;
    }
};
```

