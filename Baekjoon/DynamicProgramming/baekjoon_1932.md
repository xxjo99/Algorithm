# 백준 1932 - 정수삼각형
- https://www.acmicpc.net/problem/1149

## 코드
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

	static int[][] arr;
	static Integer[][] dp;
	static int n;

	static int recur(int depth, int idx) {
		if (depth == n - 1) {
			return dp[depth][idx];
		}

		if (dp[depth][idx] == null) {
			dp[depth][idx] = Math.max(recur(depth + 1, idx), recur(depth + 1, idx + 1)) + arr[depth][idx];
		}
		return dp[depth][idx];

	}

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		n = Integer.parseInt(br.readLine());

		arr = new int[n][n];
		dp = new Integer[n][n];

		for (int i = 0; i < n; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine(), " ");

			for (int j = 0; j < i + 1; j++) {
				arr[i][j] = Integer.parseInt(st.nextToken());
			}
		}

		for (int i = 0; i < n; i++) {
			dp[n - 1][i] = arr[n - 1][i];
		}
		
		System.out.println(recur(0, 0));

	}

}
```

## 풀이
정삼각형꼴로 나열되있는 수의 배열에서 맨 위층에서 시작해 아래층으로 내려가면서 하나씩 더해가며 최종적으로 더한 값중 최대값을 구해야하는 문제

이 문제의 경우 가장 위의 값부터 시작하는 것이 아닌 삼각형의 가장 아래의 수들부터 차례대로 더해나가며 가장 큰 값을 구하면 된다. 

그렇게되면 dp[0][0]에는 누적합이 가장 큰 값이 위치하게 될 것이다.

```	
static int[][] arr;
static Integer[][] dp;

for (int i = 0; i < n; i++) {
  StringTokenizer st = new StringTokenizer(br.readLine(), " ");

  for (int j = 0; j < i + 1; j++) {
    arr[i][j] = Integer.parseInt(st.nextToken());
  }
}

for (int i = 0; i < n; i++) {
  dp[n - 1][i] = arr[n - 1][i];
}
```
제시된 값이 저장될 배열 arr, 누적합이 저장될 배열 dp를 생성한다.

arr에 값을 저장하고 dp에도 정삼각형 밑변에 위치한 수들이 저장되야하므로 dp에 arr과 똑같은 값들을 넣어준다.

```
static int recur(int depth, int idx) {
  if (depth == n - 1) {
    return dp[depth][idx];
  }

  if (dp[depth][idx] == null) {
    dp[depth][idx] = Math.max(recur(depth + 1, idx), recur(depth + 1, idx + 1)) + arr[depth][idx];
  }
  return dp[depth][idx];

}
```
그리고 최대값을 찾기위한 재귀함수를 구현해준다. 재귀함수에 넘겨줄 인자로는 현재 깊이를 나타내는 depth, 
현재의 깊이에서 탐색할 위치를 나타내는 idx 두개를 인자로 넘겨준다.

만약 가장 꼭대기까지 탐색이 완료됐다면(depth == n - 1) 그 값을 반환해준다.

그렇지않고 탐색되지 않았던 값이라면 다음 행의 양쪽 값을 비교해서 둘 중 최대값을 넣어준다.

연산이 완료됐다면 정삼각형의 꼭대기의 수를 반환해주고 출력하면 된다.


