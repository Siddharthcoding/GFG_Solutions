# Using inorder traversal

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    void inorder(Node *root, vector<int>&nums) {
        if(!root)
        return;
        
        inorder(root->left, nums);
        nums.push_back(root->data);
        inorder(root->right, nums);
    }
  
    bool isSymmetric(Node* root) {
        // Code here
        vector<int>nums;
        inorder(root, nums);
        
        int i = 0, j = nums.size()-1;
        while(i < j) {
            if(nums[i] != nums[j])
            return false;
            
            i++;
            j--;
        }
        
        return true;
    }
};
```