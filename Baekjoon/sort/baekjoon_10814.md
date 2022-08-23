# 백준 2751 - 수 정렬하기 2
- https://www.acmicpc.net/problem/1436

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

Arrays.sort()를 사용하면 시간초과가 나온다.

문제를 풀기위해서는 O(nlogn)의 시간복잡도가 나와야하지만 Arrays.sort()는 최악의 경우 O(n^2)이 나오기때문이다.

그렇기때문에 Collections 클래스의 메소드인 Collections.sort()와 StringBuilder을 사용한다.

StringBuilder의 경우 문자열을 더할 때 기존의 데이터에 더하게 되므로 속도가 빠르다.
