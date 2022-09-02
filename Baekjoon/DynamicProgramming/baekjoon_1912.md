# 백준 1912 - 연속합
- https://www.acmicpc.net/problem/1912

## 코드
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
	
	static int[] arr;
	static Integer[] dp;
	static int max;
	
	public static int recur (int n) {
		if (dp[n] == null) {
			dp[n] = Math.max(recur(n - 1) + arr[n], arr[n]);
			max = Math.max(dp[n], max);
		}
		
		return dp[n];
	}

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int n = Integer.parseInt(br.readLine());
		
		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		
		arr = new int[n];
		dp = new Integer[n];
		
		for(int i = 0; i < n; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		
		dp[0] = arr[0];
		max = arr[0];
		
		recur(n - 1);
		System.out.println(max);
		
	}

}
```

## 풀이
연속된 숫자의 합중 가장 큰값을 구하면 된다. 그러므로 연속된 값만 생각하면 된다.

메모이제이션을 이용해서 이전까지 탐색해서 더한 값과 현재의 값을 비교해서 더큰 값을 dp배열에 저장해나가는 방식으로 해결하면 된다.

```
static int[] arr;
static Integer[] dp;
static int max;
  
dp[0] = arr[0];
max = arr[0];
```
먼저 제시된 값이 저장될 배열 arr과 연속합을 저장할 dp배열, 최대값을 저장할 max변수를 생성해두었다.

dp의 첫번째 값은 제시된 값의 첫번째 값과 동일하므로 arr[0]을 저장해두었고, 지금까지의 최대값은 arr[0]이므로 max또한 설정해두었다.

```
public static int recur (int n) {
  if (dp[n] == null) {
    dp[n] = Math.max(recur(n - 1) + arr[n], arr[n]);
    max = Math.max(dp[n], max);
  }

  return dp[n];
}
```

다음은 재귀함수를 구현해서 최대값을 판별해준다.

만약 dp[n]에 저장된 값이 없다면 이전까지 탐색해 더한값 + 현재값, 현재값 두개의 값을 비교해서 더 큰 값을 dp배열에 저장하고,
최대값과 dp배열의 값을 비교해준다.

연산이 완료됐다면 dp[n]값을 반환해주고 최대값을 출력해주면 된다.


