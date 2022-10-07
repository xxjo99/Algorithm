# leetcode - Length of Last Word
leetcode 58. [Length of Last Word](https://leetcode.com/problems/length-of-last-word/)

## 코드
```java
class Solution {
    public int lengthOfLastWord(String s) {
        String[] arr = s.split(" ");
        return arr.length == 0 ? 0 : arr[arr.length-1].length();
    }
}
```

## 풀이
주어진 문자열에서 마지막 공백 뒤의 문자열의 길이를 구하는 문제

배열을 생성하고 문자열을 split를 통해 공백을 기준으로 나누어 넣어준디.

그 후 삼항연산자를 통해 배열에 아무것도 없다면 0을 반환하고, 그렇지 않다면 배열의 마지막 원소의 길이를 반환해주면 된다.
