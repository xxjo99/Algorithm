# 백준 15649 - N과 M (1)
- https://www.acmicpc.net/problem/15649

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

	static int[] arr;
	static boolean[] visit;
	
	public static void dfs(int n, int m, int depth) {
		if (depth == m) {
			for (int i : arr) {
				System.out.print(i + " ");
			}
			System.out.println();
			return;
		}
		
		for (int i = 0; i < n; i++) {
			if (!visit[i]) {
				visit[i] = true;
				arr[depth] = i + 1;
				dfs(n, m, depth + 1);
				visit[i] = false;
			}
		}
		
	}
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		int n = Integer.parseInt(st.nextToken());
		int m = Integer.parseInt(st.nextToken());
		
		arr = new int[m];
		visit = new boolean[n];
		dfs(n, m, 0);
		
	}
	
}
```

## 풀이
백트래킹 문제

백트래킹의 방법 중 하나인 DFS를 사용해서 풀면된다.

방문한 노드를 검사할 수 있는 n크기의 boolean배열, 값을 담을 m크기의 arr 배열을 생성한다. 

```
dfs(n, m, 0);
```
그리고 dfs함수를 호출하는데 dfs함수에는 n과 m 그리고 깊이를 나타내는 depth를 인자로 주고 실행시킨다. 이때 depth는 0부터 시작한다.

```
public static void dfs(int n, int m, int depth) {
	if (depth == m) {
		for (int i : arr) {
			System.out.print(i + " ");
		}
		System.out.println();
		return;
	}

	for (int i = 0; i < n; i++) {
		if (!visit[i]) {
			visit[i] = true;
			arr[depth] = i + 1;
			dfs(n, m, depth + 1);
			visit[i] = false;
		}
	}

}
```

n번의 반복문을 돌면서 만약 노드를 방문하지 않았다면 (visit[i] == false) 
해당노드를 true로 변경, 깊이에 해당하는 arr의 인덱스에 값을 저장하고 자식노드의 방문을 위해 depth를 1 증가시켜 재귀호출한다.

자식노드 방문이 끝났다면 visit를 false로 변경해 방문하지 않은 상태로 변경한다.

재귀호출을 하면서 depth가 m과 같아졌다면 arr의 값을 출력시키면 된다.
