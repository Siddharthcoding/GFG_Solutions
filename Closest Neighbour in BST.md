# Just brute force traversing BST

## Time Complexity : O()

``` cpp []
class Solution {
  public:
    int findMaxFork(Node* root, int k) {
        // code here
        int ans = -1;
        
        while(root) {
            if(root->data <= k) {
                ans = root->data;
                root = root->right;
            } else {
                root = root->left;
            }
        }
        
        return ans;
    }
};
```