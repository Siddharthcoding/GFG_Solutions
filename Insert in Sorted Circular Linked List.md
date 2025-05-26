# Traverse to find correct position of node while maintaining the circular linked list property 

## Time Complexity : O(N)

``` cpp []
class Solution {
    public: 
    Node *sortedInsert(Node *head, int data) {
        
        Node *node = new Node(data);
        
        if(data < head->data){
            Node *tail = head;
            
            while(tail->next != head) 
            tail = tail->next;
            
            node->next = head;
            tail->next = node;
            
            head = node;
            return head;
        }else{
            Node *temp = head;
            while(temp->next->data < data && temp->next != head){
                temp = temp->next;
            }
            
            if(temp->next == head){
                temp->next = node;
                node->next = head;
            }else{
                node->next = temp->next;
                temp->next = node;
            }
            
            return head;
        }
    }
};
```

