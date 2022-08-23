# 백준 10814 - 나이순 정렬
- https://www.acmicpc.net/problem/10814

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

		String[][] arr = new String[n][2];
		StringBuilder sb = new StringBuilder();

		for (int i = 0; i < n; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			arr[i][0] = st.nextToken();
			arr[i][1] = st.nextToken();
		}

		Arrays.sort(arr, new Comparator<String[]>() {
			@Override
			public int compare(String[] s1, String[] s2) {
				return Integer.parseInt(s1[0]) - Integer.parseInt(s2[0]);
			}
		});

		for (int i = 0; i < n; i++) {
			sb.append(arr[i][0]).append(" ").append(arr[i][1]).append("\n");
		}

		System.out.println(sb);

	}

}
```

## 풀이
정렬문제

나이를 오름차순으로, 같은 나이일경우 입력된 순서대로 정렬해야 한다.

```
Arrays.sort(arr, new Comparator<String[]>() {
	@Override
	public int compare(String[] s1, String[] s2) {
		return Integer.parseInt(s1[0]) - Integer.parseInt(s2[0]);
	}
});
```

이차원 배열을 생성해 값을 넣고 Arrays.sort()를 사용해 나이 순서대로 정렬한다.

Comparator의 compare를 override해서 두 값의 위치를 바꿀지 말지 결정한다. s1과 s2의 차를 return해서 차가 같다면 바꾸지 않고 그렇지 않다면 두 값의 위치를 바꾼다. 
