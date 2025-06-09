# Finding range of values in the tree, if it collapses at a point it is dead end

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    bool find(Node* root, int minVal, int maxVal) {
        if (!root) 
        return false;

        if (minVal == maxVal) 
        return true;

        return find(root->left, minVal, root->data - 1) ||
               find(root->right, root->data + 1, maxVal);
    }
  
    bool isDeadEnd(Node *root) {
        // Code here
        
        return find(root, 1, INT_MAX);
    }
};
```