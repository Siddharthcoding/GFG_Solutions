# Using Floyd's cycle detection algorithm

## Time Complexity : O(N)

``` cpp []
class Solution {
  public:
    // Function to find the length of a loop in the linked list.
    int countNodesinLoop(Node *head) {
        // Code here
        bool hasLoop = false;
        
        Node *slow = head, *fast = head;
        
        while(fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
            
            if(slow == fast) {
                hasLoop = true;
                break;
            }
        }
        
        if(!hasLoop)
        return 0;
        else {
            int count = 1;
            while(fast->next != slow) {
                count++;
                fast = fast->next;
            }
            
            return count;
        }
    }
};
```

