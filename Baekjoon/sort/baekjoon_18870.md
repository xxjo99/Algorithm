# 백준 18870 - 좌표압축
- https://www.acmicpc.net/problem/18870

## 코드
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.HashMap;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(br.readLine());
		
		int[] origin = new int[n];
		int[] sorted = new int[n];
		
		HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
		
		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		for(int i = 0; i < n; i++) {
			sorted[i] = origin[i] = Integer.parseInt(st.nextToken());
		}
		
		Arrays.sort(sorted);
		
		int rank = 0;
		
		for (int i : sorted) {
			
			if (!map.containsKey(i)) {
				map.put(i, rank);
				rank++;
			}
			
		}
		
		StringBuilder sb = new StringBuilder();
		for(int key : origin) {
			int num = map.get(key);
			sb.append(num).append(' ');
		}
		System.out.println(sb);

	}

}
```

## 풀이
주어진 숫자를 비교해서 그 숫자보다 작은 숫자의 개수를 출력하는 문제

먼저 원본배열과 정렬할 배열, HaspMap을 생성한다. HashMap을 통해 정렬된 배열의 특정 원소보다 작은 수의 개수를 확인할 수 있다. 
중복된 원소가 있다면 서로 같은 값을 가지게된다.
```
int rank = 0;
for (int i : sorted) {			
	if (!map.containsKey(i)) {
		map.put(i, rank);
    rank++;
  }		
}
 ```
 작은 숫자의 개수를 체크해주는 rank 변수를 선언한다.
 
 정렬된 배열을 탐색하면서 중복되지 않은 원소가 나올때마다 rank를 map에 넣고 rank를 1 더해준다.
 
 ```
 for(int key : origin) {
  int num = map.get(key);
  sb.append(num).append(' ');
}
 ```
원본배열을 탐색하면서 map의 key에 해당하는 value(rank)를 가져와 StringBuilder에 저장하고 출력하면 된다. 
