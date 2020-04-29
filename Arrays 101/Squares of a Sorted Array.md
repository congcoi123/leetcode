Source: https://leetcode.com/explore/learn/card/fun-with-arrays/521/introduction/3240/

Given an array of integers A sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.

Example 1:
```
Input: [-4,-1,0,3,10]
Output: [0,1,9,16,100]
```
Example 2:
```
Input: [-7,-3,2,3,11]
Output: [4,9,9,49,121]
```

Note:
- 1 <= A.length <= 10000
- -10000 <= A[i] <= 10000
- A is sorted in non-decreasing order.

```Java
class Solution {
    public int[] sortedSquares(int[] A) {    
        int length = A.length;
        for (int i = 0; i < length; i++) {
            int temp = A[i];
            temp *= temp;
            A[i] = temp;
        }
        
        for (int i = 0; i < length - 1; i++) {
            if (A[i] > A[i + 1]) {
                insert(A, i + 1);
            }
        }
        
        return A;
    }
    
    private void swap(int[] A, int i, int j) {
        int temp = A[i];
        A[i] = A[j];
        A[j] = temp;
    }
    
    private void insert(int[] A, int index) {
        if (index > 0 && A[index - 1] > A[index]) {
            swap(A, index - 1, index);
            insert(A, --index);
        }
    }
}
```
