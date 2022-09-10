# 백준 18258 - 큐 2
- https://www.acmicpc.net/problem/18258

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int N = Integer.parseInt(br.readLine());
		int back = 0;
		Queue<Integer> q = new LinkedList<>();

		StringBuffer sb = new StringBuffer();
		for (int i = 0; i < N; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			String s = st.nextToken();

			switch (s) {
			case "push": {
				int x = Integer.parseInt(st.nextToken());
				q.add(x);
				back = x;
				break;
			}

			case "pop": {
				if (q.isEmpty()) {
					sb.append(-1).append("\n");
				} else {
					sb.append(q.poll()).append("\n");
				}
				break;
			}

			case "size": {
				sb.append(q.size()).append("\n");
				break;
			}

			case "empty": {
				if (q.isEmpty()) {
					sb.append(1).append("\n");
				} else {
					sb.append(0).append("\n");
				}
				break;
			}

			case "front": {
				if (q.isEmpty()) {
					sb.append(-1).append("\n");
				} else {
					sb.append(q.peek()).append("\n");
				}
				break;
			}

			case "back": {
				if (q.isEmpty()) {
					sb.append(-1).append("\n");
				} else {
					sb.append(back).append("\n");
				}
				break;
			}

			default:
				break;
			}
		}
		System.out.println(sb);

	}

}
```

## 풀이
큐를 구현하고 명령어를 처리하는 프로그램을 작성하는 문제.

내장 라이브러리인 Queue를 사용하면 된다.

```
int back = 0;
Queue<Integer> q = new LinkedList<>();

StringBuffer sb = new StringBuffer();
for (int i = 0; i < N; i++) {
  StringTokenizer st = new StringTokenizer(br.readLine());
  String s = st.nextToken();

  switch (s) {
  case "push": {
    int x = Integer.parseInt(st.nextToken());
    q.add(x);
    back = x;
    break;
  }

  case "pop": {
    if (q.isEmpty()) {
      sb.append(-1).append("\n");
    } else {
      sb.append(q.poll()).append("\n");
    }
    break;
  }

  case "size": {
    sb.append(q.size()).append("\n");
    break;
  }

  case "empty": {
    if (q.isEmpty()) {
      sb.append(1).append("\n");
    } else {
      sb.append(0).append("\n");
    }
    break;
  }

  case "front": {
    if (q.isEmpty()) {
      sb.append(-1).append("\n");
    } else {
      sb.append(q.peek()).append("\n");
    }
    break;
  }

  case "back": {
    if (q.isEmpty()) {
      sb.append(-1).append("\n");
    } else {
      sb.append(back).append("\n");
    }
    break;
  }

  default:
    break;
  }
}
System.out.println(sb);
```
back 명령어를 처리할때 사용할 back 변수와 Queue를 생성한다.

그리고 입력받은 횟수만큼 반복하면서 switch문을 사용해 명령어를 처리해준다.

만약 push라면 정수x를 입력받고 add()를 사용해 x를 큐에 저장한다. x는 back 명령어를 처리하기 위해 back에도 저장해준다.

pop라면 먼저 isEmpty()를 사용해 큐가 비어있는지 확인해준다. 비어있다면 -1을 출력하고 그렇지 않다면 poll()로 정수를 삭제하고 StringBuilder에 저장해준다.

size라면 size()를 사용해 크기를 확인해주고 empty라면 isEmpty()를 사용해 비어있는지 확인해준다.

front라면 비어있는지 확인하고 비어있지 않다면 peek()를 사용해 가장 앞의 정수를 출력해준다.

back라면 비어있는지 확인하고 비어있지 않다면 back변수에 저장된 수를 출력해주면 된다.
