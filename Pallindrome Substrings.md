# Brute Force Solution

## Time Complexity : O(N^3)

```cpp []
class Solution {
  public:
    bool isPallindrome(string str) {
        if(str.size() < 2)
        return false;
        
        int i = 0, j = str.size()-1;
        
        while(i < j) {
            if(str[i] != str[j])
            return false;
            
            i++;
            j--;
        }
        
        return true;
    }
  
    int countPS(string &s) {
        // code here
        int count = 0;
        
        for(int i = 0; i < s.size(); i++) {
            string temp = "";
            for(int j =i; j < s.size(); j++) {
                temp += s[j];
                if(isPallindrome(temp)) {
                    count++;
                }
            }
        }
        
        return count;
    }
};
```

# Optimized Solution(Using Expand Around Center)

## Time Complexity : O(N^2)

```cpp []
class Solution {
  public:
    int expand(const string &s, int left, int right) {
        int n = s.size();
        int count = 0;
    
        while (left >= 0 && right < n && s[left] == s[right]) {
            if (right - left + 1 >= 2) {
                count++;
            }
            left--;
            right++;
        }
    
        return count;
    }
  
    int countPS(string &s) {
        // code here
        int n = s.size();
        int count = 0;

        for (int i = 0; i < n; i++) {
            count += expand(s, i, i + 1);
            count += expand(s, i, i + 2);
        }
        
        return count;
    }
};
```