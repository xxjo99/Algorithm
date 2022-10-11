# leetcode - Add Binary
leetcode 67. [Add Binary](https://leetcode.com/problems/add-binary/)

## 코드
```java
class Solution {
    public String addBinary(String a, String b) {
        int ba = Integer.parseInt(a, 2);
        int bb = Integer.parseInt(b, 2);
        
        int c = ba + bb;
        
        String result = Integer.toBinaryString(c);
        return result;
    }
}
```

## 풀이
2진수로 주어진 두 수를 더해서 같은 2진수로 반환하는 문제.

먼저 주어진 두 2진수 a와 b를 Integer.parseInt를 이용해서 2진수를 10진수로 바꾸고 두 수를 더해준다.

그리고 더한 값을 Integer.toBinaryString 를 사용해 이진수로 변경하고 반환해주면 된다.
