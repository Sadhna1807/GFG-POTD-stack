# GFG-POTD-stack
i will solve gfg potd consistency upto 60 days
day 1>
problem - The Painter's Partition Problem-II
class Solution {
  public:
  bool isFeasible(const vector<int>& boards, int k, long long maxTime) {
    int paintersCount = 1;
    long long currentBoardSum = 0;

    for (int board : boards) {
     
        if (board > maxTime) return false;

        if (currentBoardSum + board <= maxTime) {
            currentBoardSum += board;
        } else {
            
            paintersCount++;
            currentBoardSum = board;
            
           
            if (paintersCount > k) return false;
        }
    }
    return true;
}

int minTime(vector<int>& arr, int k) {
    int n = arr.size();
    if (n == 0) return 0;

   
    long long low = *max_element(arr.begin(), arr.end()); 
    long long high = accumulate(arr.begin(), arr.end(), 0LL); 
    long long result = high;

    while (low <= high) {
        long long mid = low + (high - low) / 2;

        if (isFeasible(arr, k, mid)) {
            result = mid;    
            high = mid - 1;  
        } else {
            low = mid + 1;   
        }
    }
    return result;     
    }
};
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/85d43951-e6b7-48e2-a414-3ef858d44231" />
