# Generating next term by counting contiguos repeating digits in previous term

## Time Complexity : O(N * L)  , where L = length of final string

``` cpp []
class Solution {
  public:
    string countAndSay(int n) {
        // code here
        string ans = "1";
        n--;
        
        while(n--) {
            int i = 0, j = 0, count = 0;
            
            string curr = "";
            while(j < ans.size()) {
                if(ans[i] == ans[j]) {
                    count++;
                    j++;
                } else {
                    curr += to_string(count);
                    curr += ans[i];
                    i = j;
                    count = 0;
                }
            }
            
            curr += to_string(count);
            curr += ans[i];
            i = j;
            count = 0;
            
            ans = curr;
            curr = "";
        }
        
        return ans;
    }
};
```

