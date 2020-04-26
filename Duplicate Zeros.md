Source: https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/3245/

Given a fixed length array arr of integers, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written.

Do the above modifications to the input array in place, do not return anything from your function.

Example 1:
```
Input: [1,0,2,3,0,4,5,0]
Output: null
Explanation: After calling your function, the input array is modified to: [1,0,0,2,3,0,0,4]
```
Example 2:
```
Input: [1,2,3]
Output: null
Explanation: After calling your function, the input array is modified to: [1,2,3]
``` 
Note:
- 1 <= arr.length <= 10000
- 0 <= arr[i] <= 9

```Java
class Solution {
    public void duplicateZeros(int[] arr) {
        int[] counterIndices = countNumberOfZeros(arr);
        int counterIndicesLength = counterIndices.length;
        if (counterIndicesLength > 0) {
            int length = arr.length;
            int oldArr[] = new int[length];
            for (int i = 0; i < length; i++) {
                oldArr[i] = arr[i];
            }
            
            int temp = 0;
            for (int i = 0; i < length; i++) {
                if (temp > length - 1) {
                    return;
                }
                arr[temp] = oldArr[i];
                if (isZeroPosition(counterIndices, i)) {
                    if (temp + 1 > length - 1) {
                        return;
                    }
                    arr[++temp] = 0;
                }
                temp++;
            }
        }
    }
    
    private boolean isZeroPosition(int[] counterIndices, int index) {
        for (int z : counterIndices) {
            if (z == index) {
                return true;
            }
        }
        return false;
    }
    
    private int[] countNumberOfZeros(int[] arr) {
        int length = arr.length;
        int counter = 0;
        for (int i = 0; i < length; i++) {
            if (arr[i] == 0) {
                counter++;
            }
        }
        int counterIndices[] = new int[counter];
        counter = 0;
        for (int i = 0; i < length; i++) {
            if (arr[i] == 0) {
                counterIndices[counter] = i;
                counter++;
            }
        }
        return counterIndices;
    }
}
```
