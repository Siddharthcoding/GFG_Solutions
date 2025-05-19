# Traversing BST to find key and the predecessor and successor

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    vector<Node*> findPreSuc(Node* root, int key) {
        Node *pre = NULL, *succ = NULL, *curr = root;

        while (curr) {
            if (curr->data == key) {
                if (curr->left) {
                    pre = curr->left;
                    while (pre->right)
                        pre = pre->right;
                }
                if (curr->right) {
                    succ = curr->right;
                    while (succ->left)
                        succ = succ->left;
                }
                break;
            }
            else if (key < curr->data) {
                succ = curr;        
                curr = curr->left;
            } else {
                pre = curr;       
                curr = curr->right;
            }
        }

        return {pre, succ};
    }
};
```

