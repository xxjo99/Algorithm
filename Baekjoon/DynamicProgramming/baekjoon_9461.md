# 백준 9461 - 파도반수열
- https://www.acmicpc.net/problem/9461

## 코드
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
	
	public static Long[] dp = new Long[101];
	
	public static long recur(int n) {
		if (dp[n] == null) {
			dp[n] = recur(n - 2) + recur(n - 3);
		}
		
		return dp[n];
	}

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		dp[0] = 0L;
		dp[1] = 1L;
		dp[2] = 1L;
		dp[3] = 1L;
		
		int n = Integer.parseInt(br.readLine());
		
		for (int i = 0; i < n; i++) {
			int a = Integer.parseInt(br.readLine());
			
			System.out.println(recur(a));
		}
		
	}

}

```
파도반 수열 문제, 동적계획법을 활용하는 문제

P(n)의 규칙을 P(1)부터 차례대로 생각해보면 1, 1, 1, 2, 2, 3, 4, 5, ... 이 나온다.

이를 수식으로 표현하면 P(n) = P(n - 2) + P(n - 3)이 나오므로 이를 적용시켜 풀면된다.

그러나 파도반 수열의 n값을 늘려가다보면 int의 범위를 넘어서게 되므로 long타입으로 계산을 해주어야 한다.

```
public static Long[] dp = new Long[101];

public static long recur(int n) {
  if (dp[n] == null) {
    dp[n] = recur(n - 2) + recur(n - 3);
  }

  return dp[n];
}
```
파도반 수열을 저장할 Long타입의 dp배열을 생성한다. n의 범위는 100까지이므로 0~100을 담아야하기때문에 배열의 크기를 101로 선언해주었다.

다음 재귀를 사용한 함수를 만들어준다.

만약 dp[n]에 저장된 값이 없다면 앞서 설명한 수식을 대입해 dp에 그 값을 저장해준다. 재귀가 끝나면 dp[n]값을 반환해주면 된다.
