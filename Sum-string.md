# Using Recursion

## Time Complexity : O(N^3)

``` cpp []
class Solution {
public:
    string addStrings(string a, string b) {
        string res = "";
        int carry = 0, i = a.size() - 1, j = b.size() - 1;

        while (i >= 0 || j >= 0 || carry) {
            int sum = carry;
            if (i >= 0) 
            sum += a[i--] - '0';
            
            if (j >= 0) 
            sum += b[j--] - '0';
            
            res += (sum % 10) + '0';
            carry = sum / 10;
        }

        reverse(res.begin(), res.end());
        return res;
    }

    bool isValid(string &s, int start, string a, string b) {
        if (start == s.length()) 
        return true;

        string sum = addStrings(a, b);
        int len = sum.length();

        if (start + len > s.length()) 
        return false;
        
        if (s.substr(start, len) != sum) 
        return false;

        return isValid(s, start + len, b, sum);
    }

    bool isSumString(string s) {
        int n = s.length();

        for (int len1 = 1; len1 <= n / 2; len1++) {
            string a = s.substr(0, len1);
            
            if (a.length() > 1 && a[0] == '0') 
            continue;

            for (int len2 = 1; len1 + len2 < n; len2++) {
                string b = s.substr(len1, len2);
                
                if (b.length() > 1 && b[0] == '0') 
                continue;

                if (isValid(s, len1 + len2, a, b)) 
                return true;
            }
        }

        return false;
    }
};
```