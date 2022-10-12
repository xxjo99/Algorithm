# leetcode - climbing stairs
leetcode 70. [climbing stairs](https://leetcode.com/problems/climbing-stairs/)

## 코드
```java
class Solution {
    public int dp(int n, int[] t) {
        if (n == 1 ) {
            return 1;
        }

        if (n == 0) {
            return 1;
        }

        if(t[n] != 0) {
            return t[n];
        }

        int a = dp(n-1, t);
        int b = dp(n-2, t);

        return t[n] = a + b;
    }

    public int climbStairs(int n) {
        int[] t = new int[n+1];
        t[0] = t[1] = 1;
        int result = dp(n, t);
        return result;
    }
}
```

## 풀이
계단을 한번에 한개 또는 두개씩 오를 수 있을 때 n 개의 계단을 오르는 모든 경우의 수를 구하는 문제. dp를 이용해 해결하면 된다.
```
public int dp(int n, int[] t) {
    if (n == 1 ) {
        return 1;
    }

    if (n == 0) {
        return 1;
    }

    if(t[n] != 0) {
        return t[n];
    }

    int a = dp(n-1, t);
    int b = dp(n-2, t);

    return t[n] = a + b;
}
 ```
 dp 메소드를 작성한다. 입력받은 값 n, dp결과값을 저장할 배열 t를 인자로 받는다.
 
 입력받은 수가 1일경우 1을 반환하고, t[n]값이 0이 아닐경우 t[n]을 반환해준다.
 
 그리고 연산을 해주면 되는데 n개의 계단을 오르는 경우의 수는 n-1의 값과 n-2의 값을 더해주면 된다.
 
 그러므로 dp(n-1)과 dp(n-2)를 더한 결과값을 반환해주면 된다.
