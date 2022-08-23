# 백준 1181 - 단어정렬
- https://www.acmicpc.net/problem/1181

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.Comparator;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(br.readLine());

		String[] arr = new String[n];

		for (int i = 0; i < n; i++) {
			arr[i] = br.readLine();
		}

		Arrays.sort(arr, new Comparator<String>() {
			@Override
			public int compare(String s1, String s2) {
				if (s1.length() == s2.length()) { // 길이가 같다면
					return s1.compareTo(s2); // 사전순으로
				} else {
					return s1.length() - s2.length();
				}
			}
		});

		System.out.println(arr[0]);
		for (int i = 1; i < n; i++) {
			if (arr[i].equals(arr[i - 1])) {
				continue;
			}

			System.out.println(arr[i]);
		}

	}

}
```

## 풀이
정렬문제

길이가 짧은 단어부터 정렬하고 같다면 사전순으로 정렬하는 문제

Arrays.sort와 Comparator을 사용하면 된다.
```
Arrays.sort(arr, new Comparator<String>() {
	@Override
	public int compare(String s1, String s2) {
		if (s1.length() == s2.length()) { // 길이가 같다면
			return s1.compareTo(s2); // 사전순으로
		} else {
			return s1.length() - s2.length();
		}
	}
});
```
Arrays,sort()를 사용해 정렬하고, Comparator의 compare를 override한다. 

s1과 s2 두 문자열을 비교해서 길이가 같다면 사전순으로, 그렇지 않다면 두 문자열의 차를 구해서 양수라면 두 문자열의 위치가 서로 바뀌고 그렇지 않디면 위치가 바뀌지 않는다.

```
System.out.println(arr[0]);
for (int i = 1; i < n; i++) {
	if (arr[i].equals(arr[i - 1])) {
		continue;
	}
	System.out.println(arr[i]);
}
```
출력의 조건에 같은 단어가 여러번 입력될 경우 한 번씩만 출력하라고 제시되어있다.

정렬된 배열의 첫번째 문자열은 비교할 필요가 없으므로 출력한다. 그 뒤부터 비교하면서 해당 문자열이 전 문자열과 같다면 continue, 그렇지 않다면 출력한다.
