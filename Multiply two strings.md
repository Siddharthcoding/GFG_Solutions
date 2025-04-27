# Multiplying digit by digit

## Time Complexity : O(N*M)

``` cpp []
class Solution {
  public:
    /*You are required to complete below function */
    string multiplyStrings(string &s1, string &s2) {
        bool negative = false;
        if (s1[0] == '-') {
            negative = !negative;
            s1 = s1.substr(1);  
        }
        if (s2[0] == '-') {
            negative = !negative;
            s2 = s2.substr(1);  
        }
    
        int len1 = s1.size(), len2 = s2.size();
        vector<int> result(len1 + len2, 0);
    
        for (int i = len1 - 1; i >= 0; i--) {
            for (int j = len2 - 1; j >= 0; j--) {
                int prod = (s1[i] - '0') * (s2[j] - '0');
                int pos1 = i + j;
                int pos2 = i + j + 1;
    
                int sum = prod + result[pos2];
                result[pos2] = sum % 10;
                result[pos1] += sum / 10;
            }
        }
    
        string ans = "";
        bool leadingZero = true;
    
        for (int i = 0; i < result.size(); i++) {
            if (leadingZero && result[i] == 0) {
                continue; 
            }
            leadingZero = false;
            ans += (result[i] + '0');
        }
    
        if (ans.empty()) {
            return "0"; 
        }
    
        if (negative) {
            ans = "-" + ans;
        }
    
        return ans;
    }
};
```

