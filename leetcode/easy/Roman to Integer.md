# leetcode - Roman to Integer
- https://leetcode.com/problems/roman-to-integer/

## 코드
```java
class Solution {
	public int romanToInt(String s) {
		
		int num = 0;
		int len = s.length();
		char c;

		for (int i = len - 1; i >= 0; i--) {
			c = s.charAt(i);
			
			if (c == 'I') {
				num += (num >= 5 || num >= 10) ? -1 : 1;
			} else if (c == 'V') {
				num += 5;
			} else if (c == 'X') {
				num += (num >= 50 || num >= 100) ? -10 : 10;
			} else if (c == 'L') {
				num += 50;
			} else if (c == 'C') {
				num += (num >= 500 || num >= 1000) ? -100 : 100;
			} else if (c == 'D') {
				num += 500;
			} else if (c == 'M') {
				num += 1000;
			}
		}
		return num;
	} 
```

## 풀이
로마 숫자를 아라비아 숫자로 나타내는 문제

문제에 제시된대로 로마숫자의 조합에 따라 조건문을 만들면 된다.
