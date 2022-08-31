# 백준 14888 - 연산자 끼워넣기 
- https://www.acmicpc.net/problem/14888

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
	
	static int n;
	static int[] arr;
	static int[] oper;
	
	static int max = Integer.MIN_VALUE;
	static int min = Integer.MAX_VALUE;

	public static void dfs(int num, int depth) {
		
		if (depth == n) {
			max = Math.max(max, num);
			min = Math.min(min, num);
			return;
		}
		
		for (int i = 0; i < 4; i++) {
			
			if (oper[i] > 0) {
				oper[i]--;
				
				if (i == 0) {
					dfs(num + arr[depth], depth + 1);
				} else if (i == 1) {
					dfs(num - arr[depth], depth + 1);
				} else if (i == 2) {
					dfs(num * arr[depth], depth + 1);
				} else if (i == 3) {
					dfs(num / arr[depth], depth + 1);
				}
				
				oper[i]++;
				
			}
			
		}
		
	}
 	
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		n = Integer.parseInt(br.readLine());
		
		arr = new int[n];
		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		for (int i = 0; i < n; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}

		oper = new int[4];
		
		st = new StringTokenizer(br.readLine(), " ");
		for (int i = 0; i < 4; i++) {
			oper[i] = Integer.parseInt(st.nextToken());
		}
		
		dfs(arr[0], 1);
		
		System.out.println(max);
		System.out.println(min);
		
	}

}

```

## 풀이
주어진 연산자의 개수를 이용해서 만들 수 있는 가장 큰 값과 작은 값을 구하는 문제

dfs를 이용해 풀면된다. dfs에 넘겨주는 인자는 가장 먼저들어오는 숫자인 arr[0], dfs의 깊이를 나타내는 depth를 넘겨준다
```
	public static void dfs(int num, int depth) {
		
		if (depth == n) {
			max = Math.max(max, num);
			min = Math.min(min, num);
			return;
		}
		
		for (int i = 0; i < 4; i++) {
			
			if (oper[i] > 0) {
				oper[i]--;
				
				if (i == 0) {
					dfs(num + arr[depth], depth + 1);
				} else if (i == 1) {
					dfs(num - arr[depth], depth + 1);
				} else if (i == 2) {
					dfs(num * arr[depth], depth + 1);
				} else if (i == 3) {
					dfs(num / arr[depth], depth + 1);
				}
				
				oper[i]++;
				
			}
			
		}
		
	}
```
반복문을 돌면서 각각의 연산자의 개수가 0이 될때까지 dfs를 재귀호출한다. 
재귀호출 할 때는 인자로 넘겨준 수에 arr의 값을 더해주고 깊이를 1증가시켜 재귀호출 한다.

연산하기 전에 연산자의 개수를 1 감소시키고, 연산 후에는 다시 연산자를 사용해야 하므로 1 증가시켜 연산자의 개수를 복구한다.

깊이와 배열에 넣어줬던 숫자의 개수가 같아지면 최대값, 최소값을 판별해 넣어주고 dfs가 종료되면 출력시켜주면 된다.
