# Using temporary array to store and sort the values

## Time Complexity : O(N LogN)

``` cpp []
class Solution {
  public:
    Node* segregate(Node* head) {
        // code here
        vector<int>temp;
        Node *ptr = head;
        
        while(ptr) {
            temp.push_back(ptr->data);
            ptr = ptr->next;
        }
        
        sort(temp.begin(), temp.end());
        
        int i = 0;
        ptr = head;
        while(ptr) {
            ptr->data = temp[i];
            ptr = ptr->next;
            i++;
        }
        
        return head;
    }
};
```

