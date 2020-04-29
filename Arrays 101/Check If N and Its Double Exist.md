Source: https://leetcode.com/explore/learn/card/fun-with-arrays/527/searching-for-items-in-an-array/3250/

Given an array arr of integers, check if there exists two integers N and M such that N is the double of M ( i.e. N = 2 * M).
More formally check if there exists two indices i and j such that :
- i != j
- 0 <= i, j < arr.length
- arr[i] == 2 * arr[j]

Example 1:
```
Input: arr = [10,2,5,3]
Output: true
Explanation: N = 10 is the double of M = 5,that is, 10 = 2 * 5.
```

Example 2:
```
Input: arr = [7,1,14,11]
Output: true
Explanation: N = 14 is the double of M = 7,that is, 14 = 2 * 7.
```

Example 3:
```
Input: arr = [3,1,7,11]
Output: false
Explanation: In this case does not exist N and M, such that N = 2 * M.
```

Constraints:
- 2 <= arr.length <= 500
- -10^3 <= arr[i] <= 10^3

```Java
class Solution {
    public boolean checkIfExist(int[] arr) {
        int length = arr.length;
        
        if (length < 2) {
            return false;
        }
        
        for (int i = 0; i < length; i++) {
            int searchVal = arr[i] * 2;
            if (isValueExist(arr, i, searchVal)) {
                return true;
            }
        }
        return false;
    }
    
    private boolean isValueExist(int[] arr, int exceptIndex, int val) {
        int length = arr.length;
        for (int i = 0; i < length; i++) {
            if (i != exceptIndex && arr[i] == val) {
                return true;
            }
        }
        return false;
    }
}
```
