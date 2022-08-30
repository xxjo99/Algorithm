# 백준 15650 - N과 M (4)
- https://www.acmicpc.net/problem/15652

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

	public static void dfs(int start, int depth) {

		if (depth == m) {
			for (int i = 0; i < m; i++) {
				sb.append(arr[i] + " ");
			}
			
			sb.append('\n');
			return;
		}

		for (int i = start; i <= n; i++) {
			arr[depth] = i;
			dfs(i, depth + 1);
		}

	}

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		n = Integer.parseInt(st.nextToken());
		m = Integer.parseInt(st.nextToken());

		arr = new int[m];

		dfs(1, 0);
		System.out.println(sb);

	}

}
```

## 풀이
N과 M (3) 문제에서 고른 수열은 비내림차순이라는 조건이 추가되었다.

dfs를 이용해서 풀면된다. N과 M (2)와 같이 시작을 나타내는 변수인 start와 깊이를 나타내는 depth를 인자로 넘겨주었다.

```
public static void dfs(int start, int depth) {

  if (depth == m) {
    for (int i = 0; i < m; i++) {
      sb.append(arr[i] + " ");
    }

    sb.append('\n');
    return;
  }

  for (int i = start; i <= n; i++) {
    arr[depth] = i;
    dfs(i, depth + 1);
  }

}
```
시작점 start부터 n까지 반복문을 돌면서 arr배열에 값을 저장해주고 dfs를 재귀호출한다. 

중복이 허용되고 비내림차순이므로 start는 반복문의 i변수로 설정하고 depth를 1 증가시켜 재귀호출하면 된다.

