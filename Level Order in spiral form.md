# Level order traversal using two stacks

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    vector<int> findSpiral(Node* root) {
        // code here
        stack<Node*>s1;
        stack<Node*>s2;
        
        s1.push(root);
        vector<int>ans;
        
        while(!s1.empty() || !s2.empty()) {
            if(!s1.empty()) {
                while(!s1.empty()) {
                    Node *temp = s1.top();
                    s1.pop();
                    
                    ans.push_back(temp->data);
                    
                    if(temp->right)
                    s2.push(temp->right);
                    
                    if(temp->left)
                    s2.push(temp->left);
                }
            } else {
                while(!s2.empty()) {
                    Node *temp = s2.top();
                    s2.pop();
                    
                    ans.push_back(temp->data);
                    
                    if(temp->left)
                    s1.push(temp->left);
                    
                    if(temp->right)
                    s1.push(temp->right);
                }
            }
        }
        
        return ans;
    }
};
```

