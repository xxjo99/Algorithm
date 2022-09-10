# 백준 9012 - 괄호
- https://www.acmicpc.net/problem/9012

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(br.readLine());
		
		Queue<Integer> q = new LinkedList<>();
		
		for (int i = 1; i <= n; i++) {
			q.add(i);
		}
		
		while (q.size() != 1) {
			q.poll();
			q.offer(q.poll());
		}
		
		System.out.println(q.poll());
	}

}
```

## 풀이
큐를 이용해서 푸는문제. 자바 내장 라이브러리 큐를 사용하면 쉽게 풀린다.

```
Queue<Integer> q = new LinkedList<>();

for (int i = 1; i <= n; i++) {
  q.add(i);
}

while (q.size() != 1) {
  q.poll();
  q.offer(q.poll());
}
```
##풀이

큐를 생성해주고 1부터 n까지의 숫자를 큐에 저장해준다.

그리고 프로그램의 종료조건이 카드가 한장 남았을 때이므로 size()를 통해 큐의 크기가 1인지 아닌지 확인해준다.

크기가 1이라면 poll()를 사용해 카드를 제거하고 다시한번 poll()을 통해 제거하는데 이번에 제거된 카드는 offer을 통해 큐에 다시 넣어준다.

반복해서 크기가 1이되면 종료되고 큐에 남은 카드를 출력해주면 된다.
