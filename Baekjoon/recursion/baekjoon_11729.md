# 백준 11729 - 하노이 탑 이동 순서
- https://www.acmicpc.net/problem/11729

## 코드
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main  {
	
	static int count = 0;
	public static StringBuilder sb = new StringBuilder();
	
	public static void hanoi(int n, int start, int mid, int to) {
		count++;
		
		if (n == 1) {
			sb.append(start + " " + to + "\n");
			return;
		}
		
		hanoi(n - 1, start, to, mid);
		sb.append(start + " " + to + "\n");
		hanoi(n - 1, mid, start, to);

	}
	
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int n = Integer.parseInt(br.readLine());

		hanoi(n, 1, 2, 3);
		
		System.out.println(count);
		System.out.println(sb);
	}
}

```

## 풀이
재귀함수를 사용하는 대표적인 예이다.

하노이 탑의 이동순서는 크게 3번으로 이루어진다.
1. n개의 원판중 n-1개를 첫 번째 기둥에서 두 번째 기둥으로 이동
2. 첫 번째 기둥에 남은 원판 1개를 세 번째 기둥으로 이동
3. 두번째 기둥 n-1개의 원판을 세 번째 기둥으로 이동

__원판 n개를 이동하는 문제는 n-1개로 세분화할 수 있고 결과적으로 원판 1개를 이동하는 문제가 된다.__

이를 재귀함수로 표현하면
1. hanoi(n - 1, start, to, mid);
   * n -1개를 첫 번째 기둥에서 두 번째 기둥으로 이동
2. sb.append(start + " " + to + "\n");
    * 1개를 세 번째 기둥으로 이동
3. hanoi(n - 1, mid, start, to);
    * 두 번째 기둥의 원판을 세번째 기둥으로 이동
* 원판이 한개(n = 1)라면 첫번째 기둥에서 세번째 기둥으로 바로 이동 후 return
