# 백준 9184 - 신나는 함수 실행
- https://www.acmicpc.net/problem/9184

## 코드
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

	static int dp[][][] = new int[21][21][21];

	public static int w(int a, int b, int c) {

		if (a <= 0 || b <= 0 || c <= 0) {
			return 1;
		}

		if (a > 20 || b > 20 || c > 20) {
			return w(20, 20, 20);
		}

		if (a < b && b < c) {
			if (dp[a][b][c] != 0) {
				return dp[a][b][c];
			} else {
				return dp[a][b][c] = w(a, b, c - 1) + w(a, b - 1, c - 1) - w(a, b - 1, c);
			}
		}

		if (dp[a][b][c] != 0) {
			return dp[a][b][c];
		} else {
			return dp[a][b][c] = w(a - 1, b, c) + w(a - 1, b - 1, c) + w(a - 1, b, c - 1) - w(a - 1, b - 1, c - 1);
		}

	}

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		while (true) {
			StringTokenizer st = new StringTokenizer(br.readLine(), " ");
			int a = Integer.parseInt(st.nextToken());
			int b = Integer.parseInt(st.nextToken());
			int c = Integer.parseInt(st.nextToken());

			if (a == -1 && b == -1 && c == -1) {
				break;
			}

			System.out.println("w(" + a + ", " + b + ", " + c + ") = " + w(a, b, c));
		}
	}

}
```

## 풀이
동적계획법 문제

재귀와 메모이제이션 기법을 사용해 w함수를 구현하면 된다.
```
static int dp[][][] = new int[21][21][21];

public static int w(int a, int b, int c) {

  if (a <= 0 || b <= 0 || c <= 0) {
    return 1;
  }

  if (a > 20 || b > 20 || c > 20) {
    return w(20, 20, 20);
  }

  if (a < b && b < c) {
    if (dp[a][b][c] != 0) {
      return dp[a][b][c];
    } else {
      return dp[a][b][c] = w(a, b, c - 1) + w(a, b - 1, c - 1) - w(a, b - 1, c);
    }
  }

  if (dp[a][b][c] != 0) {
    return dp[a][b][c];
  } else {
    return dp[a][b][c] = w(a - 1, b, c) + w(a - 1, b - 1, c) + w(a - 1, b, c - 1) - w(a - 1, b - 1, c - 1);
  }

}
```
먼저 메모이제이션에 사용될 dp 배열을 생성했다. 여기에는 연산이 완료된 값이 저장되게 된다.

다음 w함수를 구현한다. a, b, c가 0보다 같거나 작을때, 20보다 클때는 문제에 제시된대로 사용하면된다.

a가 b보다 작고 b가 c보다 작을때 dp배열에 값이 저장되어 있지 않을경우 (dp == 0) 값을 계산하고 해당 dp배열에 저장해준다음 반환하거나
그렇지 않고 값이 저장되있을경우 그 값을 가져와 반환해주면 된다.

그 외의 경우에도 메모이제이션 기법을 사용해 연산후에 저장하고 반환하거나 저장되있는 값을 반환해주면 해결된다.
