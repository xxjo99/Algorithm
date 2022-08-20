# 백준 7568 - 덩치
- https://www.acmicpc.net/problem/7568

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
		int[][] arr = new int[n][2];
		
		StringTokenizer st;
		for (int i = 0; i < n; i++) {
			st = new StringTokenizer(br.readLine(), " ");
			arr[i][0] = Integer.parseInt(st.nextToken()); // 몸무게
			arr[i][1] = Integer.parseInt(st.nextToken()); // 키
		}
		
		for(int i = 0; i < n; i++) {
			int rank  = 1;
			
			for(int j = 0; j < n; j++) {
				
				if(i == j) {
					continue;
				}
				
				if (arr[i][0] < arr[j][0] && arr[i][1] < arr[j][1]) {
					rank++;
				}
			}
 
			System.out.print(rank + " ");
		}
	}

}
```

## 풀이
브루트포스를 이용하는 문제이다.

키와 몸무게를 담는 2차원 배열을 생성한다.

이중 반복문 안에 rank 변수를 생성 후 몸무게와 키가 자신보다 크다면 1씩 증가시키면서 모든 인덱스를 탐색하면 된다. 

