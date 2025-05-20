# Traversing the tree to find time required to spread the fire from the target node

## Time Complexity : O(N logN)

``` cpp []
class Solution {
  public:
    int burn(Node *root, int &timer, int target) {
        if(!root)
        return 0;
        
        if(root->data == target)
        return -1;
        
        int left = burn(root->left, timer, target);
        int right = burn(root->right, timer, target);
        
        if(left < 0) {
            timer = max(timer, abs(left) + right);
            return left - 1;
        }
        
        if(right < 0) {
            timer = max(timer, abs(right) + left);
            return right - 1;
        }
        
        return 1 + max(left, right);
    }
    
    void findNode(Node *root, int target, Node *&burntNode) {
        if(!root)
        return;
        
        if(root->data == target) {
            burntNode = root;
            return;
        }
        
        findNode(root->left, target, burntNode);
        findNode(root->right, target, burntNode);
    }
    
    int findHeight(Node *root) {
        if(!root)
        return 0;
        
        return 1 + max(findHeight(root->left), findHeight(root->right));
    }
  
    int minTime(Node* root, int target) {
        // code here
        int timer = 0;
        burn(root, timer, target);
        
        Node *burntNode = NULL;
        findNode(root, target, burntNode);
        
        int height = findHeight(burntNode) - 1;
        
        return max(timer, height);
    }
};
```

