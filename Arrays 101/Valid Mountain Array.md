Source: https://leetcode.com/explore/learn/card/fun-with-arrays/527/searching-for-items-in-an-array/3251/

Given an array A of integers, return true if and only if it is a valid mountain array.
Recall that A is a mountain array if and only if:

- A.length >= 3
- There exists some i with 0 < i < A.length - 1 such that:
  - A[0] < A[1] < ... A[i-1] < A[i]
  - A[i] > A[i+1] > ... > A[A.length - 1]

Example 1:
```
Input: [2,1]
Output: false
```

Example 2:
```
Input: [3,5,5]
Output: false
```

Example 3:
```
Input: [0,3,2,1]
Output: true
```

Note:
- 0 <= A.length <= 10000
- 0 <= A[i] <= 10000 

```Java
class Solution {
    public boolean validMountainArray(int[] A) {
        int length = A.length;
        boolean flagUp = true;
        boolean checkUp = false;
        
        for (int i = 0; i < length - 1; i++) {
            // check the left side
            if (flagUp) {
                if (A[i] < A[i+1]) {
                    checkUp = true;
                } else if (A[i] == A[i+1]) {
                    return false;
                } else {
                    // check the right side
                    flagUp = false;
                }
            } else {
                if (A[i] > A[i+1]) {
                    // do nothing
                } else {
                    return false;
                }
            }
        }
        
        // if the status is not changed
        if (!checkUp || flagUp) {
            return false;
        }
        
        return true;
    }
}
```
