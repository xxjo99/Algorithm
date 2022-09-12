# 백준 11866 - 요세푸스 문제0
- https://www.acmicpc.net/problem/11866

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

		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		int n = Integer.parseInt(st.nextToken());
		int k = Integer.parseInt(st.nextToken());

		Queue<Integer> q = new LinkedList<>();

		for (int i = 0; i < n; i++) {
			q.add(i + 1);
		}

		System.out.print("<");
		while (q.size() > 0) {
			for (int i = 0; i < k - 1; i++) {
				q.add(q.poll());
			}
			
			System.out.print(q.poll());
			
			if (q.size() > 0) {
				System.out.print(", ");
			}
		}
		System.out.print(">");
	}

}
```

## 풀이
요세푸스 순열을 구하는 프로그램을 만드는 문제

내장 라이브러리를 이용하여 큐를 생성하고 큐에 1부터 입력받은 n까지의 숫자를 모두 넣는다.

```
while (q.size() > 0) {
  for (int i = 0; i < k - 1; i++) {
    q.add(q.poll());
  }

  System.out.print(q.poll());

  if (q.size() > 0) {
    System.out.print(", ");
  }
}
System.out.print(">");
}
```

큐의 맨 앞에있던 수를 제거하고 제거한 수를 다시 큐에 넣어 큐의 시작을 변경한다.

그리고 다시 큐의 맨앞의 수를 출력하고 제거한다.

이를 큐에 있는 모든 원소가 제거될 때까지 반복하면 된다.

