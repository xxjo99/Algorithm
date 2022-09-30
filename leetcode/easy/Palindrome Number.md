# leetcode - Palindrome Number
- https://leetcode.com/problems/palindrome-number/

## 코드
```java
class Solution {

	public boolean isPalindrome(int x) {
		String str = String.valueOf(x);
		StringBuilder sb = new StringBuilder(str);

		return sb.reverse().toString().equals(str) ? true : false;
    }
	
}
```

## 풀이
Palindrome Number를 판별하는 문제, Palindrome Number란 정방향과 역방향이 같은 수를 말한다.

StringBuilder에는 reverse() 함수가 있어서 문자열을 뒤집을 수 있다. 이를 사용하면 간단하게 해결할 수 있다.

```java
String str = String.valueOf(x);
StringBuilder sb = new StringBuilder(str);
```
먼저 주어진 수를 문자열로 변경하고 문자열 변수 str과 Stringbuilder 변수 sb에 저장한다.

```java
return sb.reverse().toString().equals(str) ? true : false;
```
그리고 sb에 저장된 값을 뒤집어 str과 비교해서 같은지 다른지 확인해서 Palindrome Number인지 판별하면 된다.
