# 백준 1436 - 영화감독 숌
- https://www.acmicpc.net/problem/1436

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
	
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int n = Integer.parseInt(br.readLine());
		
		int num = 666;
		int count = 0;
		
		while (true) {
			String s = Integer.toString(num);
			
			if (s.contains("666")) {
				count++;
			}
			
			if (count == n) {
				break;
			}
			
			num++;
		}
		
		System.out.println(num);
		
	}

}

```

## 풀이
브루트포스를 이용하는 간단한 문제이다.

주어진 n의 최소값은 1이므로 666부터 시작해서 1씩 올려가며,
666이 들어있을 경우 count를 1 증가시켜주고,
n과 count가 같아진다면 해당 숫자를 출력하면 된다.
