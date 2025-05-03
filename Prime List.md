# Using brute force approach checking nearest prime number for each non-prime number in the list

## Time Complexity : O(N^2)

``` cpp []
class Solution {
  public:
    bool isPrime(int num) {
        if(num <= 1)
        return false;
        
        if(num <= 3)
        return true;
        
        if (num % 2 == 0 || num % 3 == 0)
        return false;
        
        for(int i = 5; i*i <= num; i+=6) {
            if (num % i == 0 || num % (i + 2) == 0)
            return false;
        }
        
        return true;
    }
  
    Node *primeList(Node *head) {
        // code here
        Node *ptr = head;
        while(ptr) {
            int num = ptr->val;
            
            int lower = num, higher = num;
            while(true) {
                if(isPrime(lower)) {
                    ptr->val = lower;
                    break;
                }
                if(isPrime(higher)) {
                    ptr->val = higher;
                    break;
                }
                lower--;
                higher++;
            }
            
            ptr = ptr->next;
        }
        
        return head;
    }
};
```

