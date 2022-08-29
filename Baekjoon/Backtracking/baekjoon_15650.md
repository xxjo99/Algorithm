# 백준 15650 - N과 M (2)
- https://www.acmicpc.net/problem/15650

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

	static int[] arr;
	
	public static void dfs(int n, int m, int start, int depth) {
		
		if (depth == m) {
			for (int val : arr) {
				System.out.print(val + " ");
			}
			
			System.out.println();
			return;
		}
        
		for (int i = start; i <= n; i++) {
 
			arr[depth] = i;
			dfs(n, m, i + 1, depth + 1);
 
		}
		
	}
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		int n = Integer.parseInt(st.nextToken());
		int m = Integer.parseInt(st.nextToken());
		
		arr = new int[m];
		dfs(n, m, 1, 0);
		
	}
	
}
```

## 풀이
N과 M(1)과 유사한 백트래킹 문제, 고른 수열은 오름차순이어야 한다는 조건이 추가되었다

dfs함수를 통해 풀면된다.

N과 M(1)과 다르게 오름차순으로 차례대로 값을 배열에 저장하게되므로 방문한 노드를 체크하는 boolean배열이 필요가 없다. 

dfs함수에 넘겨줄 인자는 n과 m, 어디서부터 시작하는지 나타내는 변수인 start 그리고 깊이를 나타내는 depth 총 4가지를 .
```
public static void dfs(int n, int m, int start, int depth) {

  if (depth == m) {
    for (int val : arr) {
      System.out.print(val + " ");
    }

    System.out.println();
    return;
  }

  for (int i = start; i <= n; i++) {

    arr[depth] = i;
    dfs(n, m, i + 1, depth + 1);

  }

}
```
start부터 n까지 반복문을 돌면서 depth에 해당하는 arr의 인덱스에 값을 넣어주고 start에 i+1, 깊이를 1 증가시키고 재귀호출한다.

m과 depfh가 같아진다면 출력한다.

