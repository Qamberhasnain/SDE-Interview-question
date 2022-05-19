# Program to generate Pascal’s Triangle
### Problem Statement
Given an integer N, return the first N rows of Pascal’s triangle.

In Pascal’s triangle, each number is the sum of the two numbers directly above it as shown in the figure below:
![](https://lh5.googleusercontent.com/SGqPaM5UefpH-NP2uVMvPGu2XpdlRSgesdFQEP_W_6v5rbdw8S0gKXKgi0NIGtY5xjoHlLDEtgc7ICZN8PQDzpr2RPG1ebLqj_gzN_K2gQqZn3ju8dz0WSccoZnTzid22-j-_SJq=s1600)


<b>Example 1:</b>
```
Input Format: N = 5

Result:
    1
   1 1
  1 2 1
 1 3 3 1
1 4 6 4 1

Explanation: There are 5 rows in the output matrix. Each row corresponds to each one of the rows in the image shown above.
```

<h1>Solution:</h1>

```java
public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
		List<Integer> row, pre = null;
		for (int i = 0; i < numRows; ++i) {
			row = new ArrayList<Integer>();
			for (int j = 0; j <= i; ++j)
				if (j == 0 || j == i)
					row.add(1);
				else
					row.add(pre.get(j - 1) + pre.get(j));
			pre = row;
			res.add(row);
		}
		return res;
    }
```
