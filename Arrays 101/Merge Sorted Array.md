Source: https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/3253/

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:
- The number of elements initialized in nums1 and nums2 are m and n respectively.
- You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.

Example:
```
Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
```

```Java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int[] tempNums1 = new int[m];
        int[] tempNums2 = new int[n];
        
        for (int i = 0; i < m; i++) {
            tempNums1[i] = nums1[i];
        }
        for (int i = 0; i < n; i++) {
            tempNums2[i] = nums2[i];
        }
        
        int i = 0;
        int j = 0;
        int k = 0;
        while (i < m && j < n) {
            if (tempNums1[i] <= tempNums2[j]) {
                nums1[k] = tempNums1[i];
                i++;
            } else {
                nums1[k] = tempNums2[j];
                j++;
            }
            k++;
        }

        while (i < m) {
            nums1[k] = tempNums1[i];
            i++;
            k++;
        }

        while (j < n) {
            nums1[k] = tempNums2[j];
            j++;
            k++;
        }

    }
}
```
