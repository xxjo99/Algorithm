# 백준 2751 - 수 정렬하기 2
- https://www.acmicpc.net/problem/1436

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(br.readLine());

		ArrayList<Integer> list = new ArrayList<>();
		for (int i = 0; i < n; i++) {
			list.add(Integer.parseInt(br.readLine()));
		}
		
		Collections.sort(list);
		
		StringBuilder sb = new StringBuilder();
		for (int i : list) {
			sb.append(i).append("\n");
		}
		
		System.out.println(sb);

	}

}


```

## 풀이
정렬문제
Arrays.sort()를 사용하면 시간초과가 나온다.
문제를 풀기위해서는 O(nlogn)의 시간복잡도가 나와야하지만 Arrays.sort()의 경우 최악의 경우 O(n^2)이 나오기때문이다.
그렇기때문에 다른 내장정렬함수인 Collections.sort()와 StringBuilder을 사용하면 된다.
