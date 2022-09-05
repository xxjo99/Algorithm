# 백준 1931 - 회의실 배정
- https://www.acmicpc.net/problem/1931

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.Comparator;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(br.readLine());

		int[][] arr = new int[n][2];

		for (int i = 0; i < n; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine(), " ");
			arr[i][0] = Integer.parseInt(st.nextToken());
			arr[i][1] = Integer.parseInt(st.nextToken());
		}

		Arrays.sort(arr, new Comparator<int[]>() {

			@Override
			public int compare(int[] o1, int[] o2) {

				if (o1[1] == o2[1]) {
					return o1[0] - o2[0];
				}

				return o1[1] - o2[1];
			}

		});

		int answer = 0;
		int endTime = 0;

		for (int i = 0; i < n; i++) {

			if (endTime <= arr[i][0]) {
				endTime = arr[i][1];
				answer++;
			}
		}

		System.out.println(answer);

	}
}
```

## 풀이
주어진 시간 내에 겹치지않으면서 회의실을 사용할 수 있는 최대 개수를 찾는 문제, 그리디 알고리즘 문제이다.

회의의 최대개수를 구하기 위해서는 회의의 종료시간이 빠르면 더 많은 활동을 선택할 수 있는 시간이 많아지게된다.

그러므로 종료시간을 기준으로 정렬을 하고 시간이 겹치지 않으면서 가장 빨리 끝나는 회의 순서로 선택하면서 풀어가면 된다. 

```
int[][] arr = new int[n][2];

for (int i = 0; i < n; i++) {
  StringTokenizer st = new StringTokenizer(br.readLine(), " ");
  arr[i][0] = Integer.parseInt(st.nextToken());
  arr[i][1] = Integer.parseInt(st.nextToken());
}

Arrays.sort(arr, new Comparator<int[]>() {

  @Override
  public int compare(int[] o1, int[] o2) {

    if (o1[1] == o2[1]) {
      return o1[0] - o2[0];
    }

    return o1[1] - o2[1];
  }

});
```

주어진 회의의 시간을 이차원배열 arr에 저장을 했다.

그리고 Arrays.sort와 Comparator 인터페이스를 사용해서 회의의 종료시간을 기준으로 정렬할 수 있도록 Override 해주었다.

```
int answer = 0;
int endTime = 0;

for (int i = 0; i < n; i++) {

  if (endTime <= arr[i][0]) {
    endTime = arr[i][1];
    answer++;
  }
}
```

결과값이 담길 answer과 이전 종료시간을 저장할 endtime 변수를 선언해주었다.

반복문을 돌면서 이전 회의의 종료시간이 다음 회의의 시작시간보다 작거나 같다면 회의를 할 수 있으므로
종료시간을 해당 회의의 종료시간으로 갱신해주고 answer을 1 늘린다.

반복문이 끝나게되면 회의의 최대개수가 나오게 된다.
