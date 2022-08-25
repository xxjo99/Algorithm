# 백준 1620 - 나는야 포켓몬 마스터 이다솜
- https://www.acmicpc.net/problem/1620

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.HashMap;
import java.util.StringTokenizer;

public class Main {

	public static boolean isNum(String s) {
		for (int i = 0; i < s.length(); i++) {
			if (!Character.isDigit(s.charAt(i))) {
				return false;
			}
		}
		return true;
	}

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		int n = Integer.parseInt(st.nextToken());
		int m = Integer.parseInt(st.nextToken());

		HashMap<String, Integer> strMap = new HashMap<>();
		HashMap<Integer, String> intMap = new HashMap<>();
		for (int i = 1; i <= n; i++) {
			String s = br.readLine();
			strMap.put(s, i);
			intMap.put(i, s);
		}

		StringBuilder sb = new StringBuilder();
		for (int i = 0; i < m; i++) {
			String s = br.readLine();

			if (isNum(s)) {
				sb.append(intMap.get(Integer.parseInt(s)) + "\n");
			} else {
				sb.append(strMap.get(s) + "\n");
			}

		}
		
		System.out.println(sb);

	}

}

```

## 풀이
주어진 정보를 저장하고 입력한 값이 숫자라면 문자열을, 문자열이라면 숫자를 출력하는 문제

문자열과 숫자 두가지 경우의 출력이 있으므로 <Integer, String> <String, Integer> 두 가지의 HashMap을 만든다.

두 가지 형태의 HashMap에 주어진 문자열을 1부터 n까지 모두 저장한다.

이제 m번을 반복하면서 입력을 받는다.
```
public static boolean isNum(String s) {
	for (int i = 0; i < s.length(); i++) {
		if (!Character.isDigit(s.charAt(i))) {
			return false;
	  }
	}
  return true;
}
```
먼저 입력이 숫자인지 문자열인지 확인해야하므로 그에대한 메소드를 만들어준다.

받은 입력이 숫자라면 <Integer, String> 형태의 HashMap에서 value를 가져오고, 문자라면 <String, Integer>에서 value를 가져와 출력해주면 된다.
