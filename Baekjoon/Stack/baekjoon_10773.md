# 백준 10773 - 제로
- https://www.acmicpc.net/problem/10773

## 코드
``` java
import java.io.IOException;
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.Stack;

public class Main {
	
	public static void main (String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int k = Integer.parseInt(br.readLine());
		
		Stack<Integer> stk = new Stack<>();
		
		for (int i = 0; i < k; i++) {
			int n = Integer.parseInt(br.readLine());
			
			if (n == 0) {
				stk.pop();
			} else {
				stk.push(n);
			}
		}
		
		int sum = 0;
		
		for (int i : stk) {
			sum += i;
		}
		
		System.out.println(sum);

	}

}
```

## 풀이
제시된 수의 합을 구하는 문제, 단 0이 오면 가장 최근의 숫자를 지워야한다. 자바의 내장 스택을 이용해서 

