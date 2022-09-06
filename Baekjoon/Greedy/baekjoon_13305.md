# 백준 13305 - 주유소
- https://www.acmicpc.net/problem/13305

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(br.readLine());

		long[] dist = new long[n - 1];
		long[] cost = new long[n];

		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		for (int i = 0; i < n - 1; i++) {
			dist[i] = Long.parseLong(st.nextToken());
		}

		st = new StringTokenizer(br.readLine(), " ");
		for (int i = 0; i < n; i++) {
			cost[i] = Long.parseLong(st.nextToken());
		}

		long sum = 0;
		long min = cost[0];

		for (int i = 0; i < n - 1; i++) {

			if (cost[i] < min) {
				min = cost[i];
			}

			sum += (min * dist[i]);
		}

		System.out.println(sum);

	}
}
```

## 풀이
주어진 도시들의 가장 왼쪽의 도시에서 가장 오른쪽 도시로 가는 최소 비용을 구하는 문제.

도시의 개수, 도시들간의 이동 거리, 리터당 기름의 가격이 주어진다. 그리고 첫 번째 주유소에서는 무조건 주유를 해야한다.

최소 비용을 구하기 위해서는 리터당 기름의 가격이 가장 싼 도시에서 주유해야 한다. 즉 기름값이 내림차순일때 주유하면 최소비용으로 갈 수 있다.

```
long[] dist = new long[n - 1];
long[] cost = new long[n];
```
거리를 저장할 dist 배열, 리터당 기름값을 저장할 cost배열을 생성했다. int형의 범위를 초과할 수 있으므로 long타입으로 선언해주었다.

```
long sum = 0;
long min = cost[0];

for (int i = 0; i < n - 1; i++) {

  if (cost[i] < min) {
    min = cost[i];
  }

  sum += (min * dist[i]);
}
```
총 비용을 저장할 sum변수와 이전까지의 주유의 최소비용인 min변수를 생성했다. 
첫 번째 주유소에서는 무조건 주유를 해야하므로 최초의 최소비용은 cost[0]으로 선언해주었다.

반복문을 돌면서 해당 도시의 주유 비용의 min보다 쌀 경우 min을 해당 도시의 주유비용으로 갱신해준다. 그리고 sum에 비용을 계산해서 더해주면 된다.
