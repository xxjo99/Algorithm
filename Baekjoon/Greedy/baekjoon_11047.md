# 백준 11047 - 동전0
- https://www.acmicpc.net/problem/11047

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		int n = Integer.parseInt(st.nextToken());
		int k = Integer.parseInt(st.nextToken());

		int[] arr = new int[n];
		int result = 0;

		for (int i = 0; i < n; i++) {
			arr[i] = Integer.parseInt(br.readLine());
		}

		for (int i = n - 1; i >= 0; i--) {
			if (arr[i] <= k) {
				result += k / arr[i];
				k = k % arr[i];
			}
		}
		
		System.out.println(result);

	}
}
```

## 풀이
주어진 돈을 만들수 있는 동전개수의 최소값을 찾는 문제, 그리디 알고리즘 문제이다.

최소한의 개수를 만들어야 하므로 가장 큰 가치를 지닌 동전부터 탐색해야한다. 

동전의 가치는 오름차순으로 나열되어있으므로 가치가 저장된 배열의 마지막부터 탐색하면서 계산해야한다. 

```
for (int i = n - 1; i >= 0; i--) {
  if (arr[i] <= k) {
    result += k / arr[i];
    k = k % arr[i];
  }
}
```
arr에 동전의 가치를 저장했고 배열의 마지막부터 탐색하면서 만들기 위한 가치 k와 동전의 가치를 나누어주고
k를 k와 arr[i]값의 나머지로 갱신해주면서 배열을 탐색해나가면 된다.
