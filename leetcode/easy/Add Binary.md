# leetcode - Add Binary
leetcode 67. [Add Binary](https://leetcode.com/problems/add-binary/)

## 코드
```java
import java.math.BigInteger;

class Solution {
    public String addBinary(String a, String b) {
    	BigInteger bigIntegerA = new BigInteger(a, 2);
        BigInteger bigIntegerB = new BigInteger(b, 2);
        return bigIntegerA.add(bigIntegerB).toString(2);
    }
}
```

## 풀이
2진수로 주어진 두 수를 더해서 같은 2진수로 반환하는 문제.

Integer.parseInt를 이용해서 2진수를 10진수로 바꾸어 계산할 수 있지만 주어진 두 수의 최대길이가 10000을 넘어가기 때문에 int, long 범위를 넘어간다.

그렇기때문에 직접 10진수로 바꾸어 계산을 해 주어야 하지만, BigInteger을 사용하면 그럴 필요 없이 바로 10진수로 바꾸어도 범위를 초과하지 않는다.

a, b를 new BigInteger()을 통해 10진수로 바꾸어주고 더한다음 toString(2)로 2진수로 바꾸고 반환하면 된다.
