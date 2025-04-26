# Completeness and Max Heap property checking through traversal

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    int countNodes(Node *root) {
        if(root == NULL)
        return 0;
        
        return (1 + countNodes(root->left) + countNodes(root->right));
    }
  
    bool isComplete(Node *root, int i, int total) {
        if(root == NULL)
        return true;
        
        if(i >= total)
        return false;
        
        return (isComplete(root->left, 2*i+1, total) && isComplete(root->right, 2*i+2, total));
    }
    
    bool checkOrder(Node *root) {
        if(root == NULL)
        return true;
        
        if(root->left && root->data < root->left->data)
        return false;
        
        if(root->right && root->data < root->right->data)
        return false;
        
        return checkOrder(root->left) && checkOrder(root->right);
    }
  
    bool isHeap(Node* tree) {
        // code here
        int total = countNodes(tree);
        
        if(isComplete(tree, 0, total) && checkOrder(tree))
        return true;
        else
        return false;
    }
};
```

