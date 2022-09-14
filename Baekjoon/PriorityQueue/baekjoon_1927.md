# 백준 1927 - 최소 힙
- https://www.acmicpc.net/problem/1927

## 코드
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.PriorityQueue;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(br.readLine());

		PriorityQueue<Integer> q = new PriorityQueue<>();

		StringBuilder sb = new StringBuilder();
		for (int i = 0; i < n; i++) {
			int num = Integer.parseInt(br.readLine());

			if (num == 0) {
				sb.append(q.size() == 0 ? 0 : q.poll()).append('\n');
			} else {
				q.add(num);
			}
		}
		
		System.out.println(sb.toString());

	}

}
```

## 풀이
11279번 최대힙 문제와 매우 유사한 문제이다

힙을 직접 구현해 해결할 수 있지만 자바에는 우선순위큐인 PriorityQueue 내장 라이브러리를 지원한다.

PriorityQueue의 내부 요소는 힙으로 구성되어 이진트리 구조로 이루어져있다.

```
PriorityQueue<Integer> q = new PriorityQueue<>();

StringBuilder sb = new StringBuilder();
for (int i = 0; i < n; i++) {
  int num = Integer.parseInt(br.readLine());

  if (num == 0) {
    sb.append(q.size() == 0 ? 0 : q.poll()).append('\n');
  } else {
    q.add(num);
  }
}
```
먼저 PriorityQueue를 생성해준다.
PriorityQueue는 기본적으로 오름차순 정렬로 되어있으므로 가장 작은 수부터 큐에서 제거된다.

다음 반복문을 돌면서 수를 입력받고 연산을 확인한다.

만약 입력으로 0이 들어왔다면 연산을 실행해야 한다. 

일단 사이즈를 확인하고 사이즈가 0이라면 비어있다는 뜻이므로 0을 출력해주고 그렇지않다면 poll()로 가장 큰 값을 출력하고 제거해준다.

0이 아닌 다른 수라면 큐에 저장해준다.  
