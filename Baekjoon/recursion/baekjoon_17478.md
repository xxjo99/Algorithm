# 백준 17478 - 재귀함수가 뭔가요
- https://www.acmicpc.net/problem/17478

## 코드
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Recursion_17478  {
	
	static int n;
	
	public static void recur(int count, String s) {
	
        	if (count == n) {
            		System.out.println(s + "\"재귀함수가 뭔가요?\"");
            		System.out.println(s + "\"재귀함수는 자기 자신을 호출하는 함수라네\"");
            		System.out.println(s + "라고 답변하였지.");
            		return;
		}
		
		System.out.println(s + "\"재귀함수가 뭔가요?\"");
        	System.out.println(s + "\"잘 들어보게. 옛날옛날 한 산 꼭대기에 이세상 모든 지식을 통달한 선인이 있었어.");
		System.out.println(s + "마을 사람들은 모두 그 선인에게 수많은 질문을 했고, 모두 지혜롭게 대답해 주었지.");
		System.out.println(s + "그의 답은 대부분 옳았다고 하네. 그런데 어느 날, 그 선인에게 한 선비가 찾아와서 물었어.\"");

		recur(count + 1, s + "____");
		System.out.println(s + "라고 답변하였지.");
	}
	
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		n = Integer.parseInt(br.readLine());
		
		System.out.println("어느 한 컴퓨터공학과 학생이 유명한 교수님을 찾아가 물었다.");
		recur(0, "");
	}
}
```

## 풀이
재귀함수를 활용하는 문제이다.

"재귀함수가 뭔가요?" "잘 들어보게. 옛날옛날 한 산 꼭대기에 이세상 모든 지식을 통달한 선인이 있었어."
"마을 사람들은 모두 그 선인에게 수많은 질문을 했고, 모두 지혜롭게 대답해 주었지."
"그의 답은 대부분 옳았다고 하네. 그런데 어느 날, 그 선인에게 한 선비가 찾아와서 물었어."

위의 네문장이 반복되므로 재귀함수를 호출해서 반복한다.

재귀가 한번 호출될 때마다 _는 네개씩 증가하므로 더해준다.

지정한 횟수의 재귀함수가 모두 호출되면 "재귀함수는 자기 자신을 호출하는 함수라네" 문장을 출력한다.

