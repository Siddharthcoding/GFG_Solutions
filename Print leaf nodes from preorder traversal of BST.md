# Using properties of BST to store till when the left subtree is traversed and then traverse the right subtree

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    vector<int> leafNodes(vector<int>& preorder) {
        // code here
        vector<int>ans;
        stack<int>st;
        
        st.push(preorder[0]);
        for(int i = 1; i < preorder.size(); i++) {
            if(preorder[i] < st.top()) {
                st.push(preorder[i]);
            } else {
                int temp = st.top();
                int count = 0;
                
                while(!st.empty() && preorder[i] > st.top()) {
                    st.pop();
                    count++;
                }
                st.push(preorder[i]);
                
                if(count >= 2)
                ans.push_back(temp);
            }
        }
        ans.push_back(st.top());
        
        return ans;
    }
};
```

