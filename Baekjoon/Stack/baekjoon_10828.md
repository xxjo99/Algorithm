# 백준 10828 - 스택 
- https://www.acmicpc.net/problem/10828

## 코드
``` java
import java.io.IOException;
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main {
	
	public static void main (String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int n = Integer.parseInt(br.readLine());
		
		Stack<Integer> stk = new Stack<>();
		
		StringBuilder sb = new StringBuilder();
		for (int i = 0; i < n; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			String s = st.nextToken();
			
			switch (s) {
			
			case "push" :
				stk.push(Integer.parseInt(st.nextToken()));
				break;
			
			case "pop" :
				if (stk.empty()) {
					sb.append(-1 + "\n");
				} else {
					sb.append(stk.pop() + "\n");
				}
				break;
			
			case "size" :
				sb.append(stk.size() + "\n");
				break;
			
			case "empty":
				if (stk.isEmpty()) {
					sb.append(1 + "\n");
				} else {
					sb.append(0 + "\n");
				}
				break;
				
			case "top":
				if (stk.isEmpty()) {
					sb.append(-1 + "\n");
				} else {
					sb.append(stk.peek() + "\n");
				}
				break;
			}
				
		}
		
		System.out.println(sb);
	}

}
```

## 풀이
스택을 구현하고 입력받은 명령어를 처리하는 문제

자바에서 기본으로 제공되는 라이브러리인 Stack를 사용해 구현하면된다.

```
Stack<Integer> stk = new Stack<>();

StringBuilder sb = new StringBuilder();
for (int i = 0; i < n; i++) {
  StringTokenizer st = new StringTokenizer(br.readLine());
  String s = st.nextToken();

  switch (s) {

  case "push" :
    stk.push(Integer.parseInt(st.nextToken()));
    break;

  case "pop" :
    if (stk.empty()) {
      sb.append(-1 + "\n");
    } else {
      sb.append(stk.pop() + "\n");
    }
    break;

  case "size" :
    sb.append(stk.size() + "\n");
    break;

  case "empty":
    if (stk.isEmpty()) {
      sb.append(1 + "\n");
    } else {
      sb.append(0 + "\n");
    }
    break;

  case "top":
    if (stk.isEmpty()) {
      sb.append(-1 + "\n");
    } else {
      sb.append(stk.peek() + "\n");
    }
    break;
  }

}
```
먼저 Stack라이브러리를 이용해 Integer 형태의 stk을 생성하고, 결과값을 저장할 StringBuilder을 생성해주었다.

다음 반복문을 돌면서 명령어를 처리하는데 StringTokenizer 라이브러리를 이용해 명령어와 값을 나눠 처리해주었다.

먼저 명령어를 입력받는다. 명령어에 대한 처리는 switch문을 사용했다.

명령어가 push라면 값을 입력받고 push() 함수를 사용해서 스택에 저장했다.

명령어가 pop라면 isEmpty()함수를 사용해 스택이 비어있는지 확인하고 비어있다면 -1,
그렇지 않다면 pop() 함수를 사용해 스택에서 값을 삭제하고 그 값을 출력해주었다.

명령어가 size라면 size함수를 통해 스택의 크기를 출력하고, empty라면 isEmpty()함수를 통해 비어있는지 아닌지 판별해주었다.

명령어가 top라면 비어있는지 확인하고 그렇지 않다면 stk.peek()를 사용해 스택의 가장 위의 값을 출력해주었다.
