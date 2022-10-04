# leetcode - Longest Common Prefix
leetcode 20. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

## 코드
```java
import java.util.Stack;

class Solution {
	public boolean isValid(String s) {

		if (s.length() % 2 != 0) {
			return false;
		}

		Stack<Character> stack = new Stack<>();

		for (int i = 0; i < s.length(); i++) {
			char c = s.charAt(i);

			if (c == '(' || c == '{' || c == '[') {
				stack.push(c);
			} else if (stack.size() == 0) {
				return false;
			} else if (c == ')') {
				
				if (stack.pop() != '(') {
					return false;
				}
				
			} else if (c == '}') {
				
				if (stack.pop() != '{') {
					return false;
				}
				
			} else if (c == ']') {
				
				if (stack.pop() != '[') {
					return false;
				}
				
			}
		}
		return stack.size() == 0;
	}
}
```

## 풀이
괄호가 올바르게 배치되어있는지 판별하는 문제, 스택을 사용하면 된다.

```java
if (s.length() % 2 != 0) {
  return false;
}
```
만약 문자열의 길이가 홀수라면 여닫는 괄호가 올바르지 않다는 뜻이므로 false를 반환한다.

```java
Stack<Character> stack = new Stack<>();

for (int i = 0; i < s.length(); i++) {
  char c = s.charAt(i);

  if (c == '(' || c == '{' || c == '[') {
    stack.push(c);
  } else if (stack.size() == 0) {
    return false;
  } else if (c == ')') {

    if (stack.pop() != '(') {
      return false;
    }

  } else if (c == '}') {

    if (stack.pop() != '{') {
      return false;
    }

  } else if (c == ']') {

    if (stack.pop() != '[') {
      return false;
    }

  }
}
return stack.size() == 0;
}
```
괄호를 넣어줄 Character형 stack를 생성하고 반복문을 돌면서 확인해준다.

주어진 문자열에서 인덱스에 맞게 하나씩 꺼내와서 char형 변수 c에 저장해준다.

만약 c가 (, {, [ 라면 스택에 push한다.

그렇지않고 ), }, ] 라면 스택에서 하나씩 pop 해주는데 만약 각각의 닫는 괄호에서 pop을 할때,
여는 괄호가 없다면 괄호가 올바르지 않게 배치되어있다는 뜻이므로 false를 반환해준다.

확인이 끝났다면 stack의 사이즈를 확인해주어서 0일 경우만 true를 반환하도록 하면 된다.


