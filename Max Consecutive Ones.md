Source: https://leetcode.com/explore/learn/card/fun-with-arrays/521/introduction/3238/

Given a binary array, find the maximum number of consecutive 1s in this array.

Example 1:
```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```    
Note:
- The input array will only contain 0 and 1.
- The length of input array is a positive integer and will not exceed 10,000

```Java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int countMax = 0;
        int count = 0;
        int lastCount = 0;
        for (int num : nums) {
            if (num == 1) {
                count++;
                if (countMax < count) {
                    countMax = count;
                }
            } else {
                lastCount = count;
                if (countMax < lastCount) {
                    countMax = lastCount;
                }
                count = 0;
            }
        }
        return countMax;
    }
}
```
