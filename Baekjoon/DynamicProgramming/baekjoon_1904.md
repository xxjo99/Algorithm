# 백준 1904 - 01타일
- https://www.acmicpc.net/problem/1904

## 코드
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
	
	static Integer[] dp = new Integer[1000001];
 	
	public static int recur(int n) {
		
		if (dp[n] == null) {
			dp[n] = (recur(n - 1) + recur(n-2)) % 15746;
		}
		
		return dp[n];
		
	}
	
	
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int n = Integer.parseInt(br.readLine());
		
		dp[0] = 0;
		dp[1] = 1;
		dp[2] = 2;
		
		System.out.println(recur(n));
	}

}

```

## 풀이
길이가 n인 2진 수열의 개수를 15746으로 나눈 나머지를 구하는 문제, 동적계획법 문제이다.

n=1 부터 시작해서 경우의 수를 나열하면 n=1일때 1, n=2일때 2, n=3일때 3, n=4일때 5, n=5일때 8, n=6일때 13 

이렇게 나열해보면 특정한 규칙이 나온다. n=3일  경우 n=1과 n=2 일때의 개수의 합이고, n=4일 경우 n=2과 n=3 일때의 개수의 합이다.

이를 활용해서 dp를 만들면된다.

```
static Integer[] dp = new Integer[1000001];

dp[0] = 0;
dp[1] = 1;
dp[2] = 2;
```
먼저 값이 저장될 Integer타입의 dp 배열을 만들어주었다. n의 범위가 1 ≤ n ≤ 1,000,000 으로 제시되어있으므로
0부터  1,000,000까지 저장되어야하므로 배열의 크기를 1000001로 설정해주었다.

dp의 0부터 2까지는 특별한 규칙이 없으므로 직접 입력해준다.

```
public static int recur(int n) {

  if (dp[n] == null) {
    dp[n] = (recur(n - 1) + recur(n-2)) % 15746;
  }

  return dp[n];

}
```

그리고 재귀를 활용해서 함수를 만들어준다.

만약 dp에 아무런 값이 저장되어있지 않을경우 (dp[n] == null) dp배열에 값을 저장해주기 위해 앞서 설명한 규칙을 활용해 식을 만들어 재귀를 해준다.
 
연산을 완료해 값이 저장되었다면 그 값을 반환해주고 출력해주면 된다.
