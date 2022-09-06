# 백준 11399 - ATM
- https://www.acmicpc.net/problem/11399

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(br.readLine());

		int[] arr = new int[n];
		int[] result = new int[n];

		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		for (int i = 0; i < n; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		Arrays.sort(arr);

		result[0] = arr[0];

		for (int i = 1; i < n; i++) {
			result[i] = result[i - 1] + arr[i];
		}

		int sum = 0;

		for (int i = 0; i < n; i++) {
			sum += result[i];
		}
		System.out.println(sum);

	}
}
```

## 풀이
각 사람마다 ATM에서 돈을 인출하는 시간이 주어지며 각 사람이 돈을 인출하는데 필요한 시간의 합의 최솟값을 구하는 문제

사람간의 대기시간을 최소화하면 최소값을 구할 수 있다.

즉 입력받은 시간을 오름차순으로 정렬을 해주고 대기시간을 구해주면 된다.

```
int[] arr = new int[n];
int[] result = new int[n];

StringTokenizer st = new StringTokenizer(br.readLine(), " ");
for (int i = 0; i < n; i++) {
	arr[i] = Integer.parseInt(st.nextToken());
}
Arrays.sort(arr);
```
주어진 입력값을 저장할 배열 arr과 사람들이 돈을 뽑기위해 몇분 걸리는지 저장할 배열 result를 생성해주었다.
그후 입력을 받고 오름차순으로 정렬을 해야하기 때문에 Arrays.sort()를 이용해 정렬해주었다.
```
result[0] = arr[0];

for (int i = 1; i < n; i++) {
	result[i] = result[i - 1] + arr[i];
}

int sum = 0;

for (int i = 0; i < n; i++) {
	sum += result[i];
}
```

result[0]는 자신의 시간이 돈뽑는 시간과 동일하기 때문에 같은 값을 저장해준다.

두번째 사람부터 반복문을 돌면서 걸리는 시간을 계산해서 저장해준다.

그후 result의 모든값을 더해서 출력해주면 된다.
