# Rotate Image by 90 degree

### Problem Statement: 
Given a matrix, your task is to rotate the matrix by 90 degrees.

#### Examples:
```
Example 1:

Input: [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]
Explanation: Rotate the matrix simply by 90 degree clockwise and return the matrix.

Example 2:

Input: [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
Output:[[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
Explanation: Rotate the matrix simply by 90 degree clockwise and return the matrix
```

# Solution:

```java
public void rotate(int[][] matrix) {
        for(int i=0;i<matrix.length;i++) {
	 		for(int j=i;j<matrix[0].length;j++){
                int temp = 0;
                temp = matrix[i][j];
	 			matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
	 		}
	 	}
        for(int i=0;i<matrix.length;i++){
            for(int j=0;j<matrix.length/2;j++){
                int temp = 0;
                temp = matrix[i][j];
                matrix[i][j] = matrix[i][matrix.length-1-j];
                matrix[i][matrix.length-1-j] = temp;
            }
        }
    }
```

