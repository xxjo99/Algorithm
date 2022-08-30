# 백준 15650 - N과 M (3)
- https://www.acmicpc.net/problem/15651

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

	static int[] arr;
	static int n, m;
	public static StringBuilder sb = new StringBuilder();

	public static void dfs(int depth) {

		if (depth == m) {
			for (int i = 0; i < m; i++) {
				sb.append(arr[i] + " ");
			}
			
			sb.append('\n');
			return;
		}

		for (int i = 1; i <= n; i++) {
			arr[depth] = i;
			dfs(depth + 1);
		}

	}

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		n = Integer.parseInt(st.nextToken());
		m = Integer.parseInt(st.nextToken());

		arr = new int[m];

		dfs(0);
		System.out.print(sb);

	}

}

```

## 풀이
N까지의 자연수 중에서 M개를 고르는데 중복되는 수를 여러번 골라도된다. dfs를 이용해서 풀면된다.

```
	public static void dfs(int depth) {

		if (depth == m) {
			for (int i = 0; i < m; i++) {
				sb.append(arr[i] + " ");
			}
			
			sb.append('\n');
			return;
		}

		for (int i = 1; i <= n; i++) {
			arr[depth] = i;
			dfs(depth + 1);
		}

	}
```
dfs 함수를 작성한다. n까지 반복문을 돌면서 arr배열에 값을 저장하고 깊이를 1 증가시켜서 dfs를 재귀호출한다.

깊이가 m과 같아졌을때 끝내고 StringBuilder에 저장하고 함수가 종료되면 출력하면 된다.

print 함수를 사용하게 되면 시간초과가 발생한다.


