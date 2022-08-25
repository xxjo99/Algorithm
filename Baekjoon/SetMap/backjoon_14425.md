# 백준 14425 - 문자열 집합
- https://www.acmicpc.net/problem/14425

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.HashMap;
import java.util.StringTokenizer;

public class Main {
	
	public static void main(String[] args) throws IOException {
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		int n = Integer.parseInt(st.nextToken());
		int m = Integer.parseInt(st.nextToken());
		
		HashMap<String, Integer> map = new HashMap<>();
		
		for(int i = 0 ; i < n ; i++) {
			String s = br.readLine();
			map.put(s, 0);
		}
		
		int count = 0;
		
		for (int i = 0; i < m; i++) {
			String s = br.readLine();
			if (map.containsKey(s)) {
				count++;
			}
		}
    
		System.out.println(count);	
		
	}
}
```

## 풀이
집합 S에 같은 문자열이 얼마나 있는지 찾는 문제

Hashmap을 사용해 풀면된다.

<String, Integer> 형태의 HashMap을 만들고 n개의 문자열을 대입한다. HashMap의 key는 문자열로 넣는다.

다음 m개의 문자열을 입력받으며 containsKey()를 이용해 문자열이 HashMap에 포함되어있는지 확인하고 포함되어 있다면 count를 증가시키고
마지막에 count를 출력해준다.

