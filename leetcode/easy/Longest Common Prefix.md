# leetcode - Longest Common Prefix
leetcode 14. [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

## 코드
```java
class Solution {
	public String longestCommonPrefix(String[] strs) {
		String prefix = "";
		
		if (strs.length == 0) {
			return prefix;
		}
		
		prefix = strs[0];

		for (int i = 1; i < strs.length; i++) {
			String cur = strs[i];
			
			while (cur.indexOf(prefix) != 0) {
				prefix = prefix.substring(0, prefix.length() - 1);
			}
		}
		
		return prefix;
	}
}
```

## 풀이
주어진 문자열에서 공통되는 가장 긴 prefix를 찾는 문제.

먼저 prefix를 저장할 String 변수를 생성한다. 초기값은 ""로 초기화한다.

주어진 문자열이 들어있는 배열에 아무것도 없다면 초기값 그래도 prefix를 return 하면된다.

그리고 문자열을 비교해야하므로 prefix에는 주어진 배열 strs에 저장되어있는 첫번째 문자열을 저장해준다.

```java
for (int i = 1; i < strs.length; i++) {
  String cur = strs[i];

  while (cur.indexOf(prefix) != 0) {
    prefix = prefix.substring(0, prefix.length() - 1);
  }
}
```
반복문을 돌면서 prefix를 찾아준다. 

그리고 prefix와 비교할 변수 cur을 생성하고 strs에 저장된 문자열을 가져온다.

indexOf와 subString를 사용해서 문자열을 잘라주면서 prefix를 확인해준다.
