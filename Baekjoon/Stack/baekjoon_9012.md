# 백준 9012 - 괄호
- https://www.acmicpc.net/problem/9012

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int t = Integer.parseInt(br.readLine());

		for (int i = 0; i < t; i++) {
			String s = br.readLine();

			Stack<Character> stk = new Stack<Character>();

			for (int j = 0; j < s.length(); j++) {
				if (s.charAt(j) == '(') {
					stk.push(s.charAt(j));
				} else {
					if (stk.empty()) {
						stk.push(s.charAt(j));
						break;
					} else {
						stk.pop();
					}
				}
			}
			
			if (stk.empty()) {
				System.out.println("YES");
			} else {
				System.out.println("NO");
			}
			
		}

	}

}
```

## 풀이
입력받은 괄호가 올바르게 짝지어져있는지 판별하는 문제

(가 입력되었을때는 스택에 push하고 )가 입력되었을때는 스택에서 pop을 하면된다. 

단 )가 입력되었을때 스택이 비어있다면 올바르지 않은 괄호이므로 NO를 출력해주면 된다.

```
for (int i = 0; i < t; i++) {
  String s = br.readLine();

  Stack<Character> stk = new Stack<Character>();

  for (int j = 0; j < s.length(); j++) {
    if (s.charAt(j) == '(') {
      stk.push(s.charAt(j));
    } else {
      if (stk.empty()) {
        stk.push(s.charAt(j));
        break;
      } else {
        stk.pop();
      }
    }
  }

  if (stk.empty()) {
    System.out.println("YES");
  } else {
    System.out.println("NO");
  }

}
```
입력받은 횟수의 반복문을 돌면서 문자열을 입력하고 확인해준다.

먼저 Character형의 스택을 생성해주고 문자열을 확인해준다.

만약 ( 라면 스택에 push한다. 

그렇지 않고 )가 왔을경우 스택이 비어있는지 아닌지 확인해준다. 
만약 비어있다면 YES인지 NO인지 판별하기 위해 스택에 넣어주고 반복문을 끝낸다.
그렇지않다면 pop를 한다.

문자열의 확인이 끝났다면 YES인지 NO인지 판단한다. 만약 비어있다면 정상적인 문자열이므로 YES를 출력하고, 
그렇지않다면 비정상적인 문자열이므로 NO를 출력해준다.
