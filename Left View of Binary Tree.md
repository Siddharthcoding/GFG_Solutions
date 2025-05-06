# Using Level Order Traversal

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    vector<int> leftView(Node *root) {
        // code here
        if(!root)
        return {};
        
        vector<int>ans;
        queue<Node*>q;
        q.push(root);
        
        while(!q.empty()) {
            int noOfNodes = q.size();
            
            for(int i = 0; i < noOfNodes; i++) {
                Node *curr = q.front();
                q.pop();
                
                if(i == 0)
                ans.push_back(curr->data);
                
                if(curr->left)
                q.push(curr->left);
                
                if(curr->right)
                q.push(curr->right);
            }
        }
        
        return ans;
    }
};
```

