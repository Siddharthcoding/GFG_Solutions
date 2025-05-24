# Using Brute Force Logic to generate all substring and accumulating their sum

## Time Complexity : O(N^2)

``` cpp []
class Solution {
public:
    int findSum(string &s, int start, int end) {
        if (start >= s.size()) 
        return 0;

        if (end > s.size()) {
            return findSum(s, start + 1, start + 1);
        } else {
            string sub = s.substr(start, end - start);
            
            if (!sub.empty() && all_of(sub.begin(), sub.end(), ::isdigit)) {
                int currSum = stoi(sub);
                return currSum + findSum(s, start, end + 1);
            } else {
                return findSum(s, start, end + 1);
            }
        }
    }

    int sumSubstrings(string &s) {
        return findSum(s, 0, 1);
    }
};

```

