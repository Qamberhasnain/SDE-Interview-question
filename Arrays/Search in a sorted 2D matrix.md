# Search in a sorted 2D matrix

### Problem Statement:
Given an m*n 2D matrix and an integer, write a program to find if the given integer exists in the matrix. 
Given matrix has the following properties:

    Integers in each row are sorted from left to right.
    The first integer of each row is greater than the last integer of the previous row

#### Example 1:
```
Input: matrix = 
[[1,3,5,7],
 [10,11,16,20],
 [23,30,34,60]], 

target = 3

Output: true

Explanation: As the given integer(target) exists in the given 2D matrix, the function has returned true.
```

#### Example 2:
```
Input: matrix = 
[[1,3,5,7],
 [10,11,16,20],
 [23,30,34,60]], 

target = 13

Output: false

Explanation: As the given integer(target) does not exist in the given 2D matrix, the function has returned false.
```
# Solution:
This solution is for **Leetcode** as test cases have sorted elements in snake pattern.
```java
public boolean searchMatrix(int[][] matrix, int target) {
        if(matrix.length == 0) return false;
        int n = matrix.length;
        int m = matrix[0].length;
        
        int lo = 0;
        int hi = (n*m)-1;
        while(lo<=hi){
            int mid = (lo+hi)/2;
            if(matrix[mid/m][mid%m] == target) return true;
            if(matrix[mid/m][mid%m] < target){
                lo = mid + 1;
            }
            else{
                hi = mid - 1;
            }
        }
        return false;
    }
```
This solution is for **Coding Ninjas** and **GFG** as test cases are sorted but elements can be repeated or have indifferent pattern.
```java
static boolean findTargetInMatrix(ArrayList<ArrayList<Integer>> mat, int m, int n, int target) {
		int i=0;
        int j=n-1;
        while(i<m && j>=0){
            if(mat.get(i).get(j) == target) return true;
            if(mat.get(i).get(j) > target){
                j--;
            }
            else{
                i++;
            }
        }
        return false;
	}
```
