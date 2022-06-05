# Implement Pow(x,n) | X raised to the power N

### Problem Statement:
Given a double x and integer n, calculate x raised to power n. Basically Implement pow(x, n).

#### Example 1:
```
Input: x = 2.00000, n = 10

Output: 1024.00000

Explanation: You need to calculate 2.00000 raised to 10 which gives ans 1024.00000
```
#### Example 2:
```
Input: x = 2.10000, n = 3

Output: 9.26100

Explanation: You need to calculate 2.10000 raised to 3 which gives ans 9.26100
```
# Solution:
```java
public double myPow(double x, int n) {
        double d = 1.0;
        long num = n;
        if(num<0) num = num * (-1);
        while(num>0){
            if(num%2==1){
                d = d * x;
                num--;
            }
            else{
                x = x * x;
                num = num/2;
            }
        }
        if(n<0) d = (double)(1.0)/(double)(d);
        return d;
    }
```
