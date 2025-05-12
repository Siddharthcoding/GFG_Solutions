# Using Greedy approach with min heaps

## Time Complexity : O(m log m + m log n)

``` cpp []
class Solution {
  public:
    int mostBooked(int n, vector<vector<int>> &meetings) {
        // code here
        priority_queue<int, vector<int>, greater<int>>freeRooms;
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>>busyRooms;
        vector<int>freq(n, 0);
        
        sort(meetings.begin(), meetings.end());
        
        for(int i = 0; i < n; i++) {
            freeRooms.push(i);
        }
        
        for(int i = 0; i < meetings.size(); i++) {
            int startTime = meetings[i][0];
            int endTime = meetings[i][1];
            
            while(!busyRooms.empty() && busyRooms.top().first <= startTime) {
                freeRooms.push(busyRooms.top().second);
                busyRooms.pop();
            }
            
            if(!freeRooms.empty()) {
                int room = freeRooms.top();
                freeRooms.pop();
                freq[room]++;
                busyRooms.push({endTime, room});
            } else {
                int waitTime = busyRooms.top().first;
                int room = busyRooms.top().second;
                busyRooms.pop();
                
                waitTime += (endTime - startTime);
                busyRooms.push({waitTime, room});
                freq[room]++;
            }
        }
        
        int maxUsed = 0;
        for(int i = 1; i < n; i++) {
            if(freq[i] > freq[maxUsed]) 
                maxUsed = i;
        }
        
        return maxUsed;
    }
};
```

