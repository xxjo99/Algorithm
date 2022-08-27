# 백준 11478 - 서로 다른 부분 문자열의 개수
- https://www.acmicpc.net/problem/11478

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.HashSet;

public class Main {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		String s = br.readLine();

		HashSet<String> set = new HashSet<>();

		String str = "";
		
		for (int i = 0; i < s.length(); i++) {
			str = "";
			
			for (int j = i; j < s.length(); j++) {
				str += s.substring(j, j+1);
				set.add(str);
			}
		}
		
		System.out.println(set.size());
	}

}


```

## 풀이
HashSet과 부분문자열을 저장할 변수 Str을 생성한다.

반복문을 돌면서 substring를 이용해서 str에 부분문자열을 대입하고 HashSet에 모두 저장해준다.

마지막으로 HashSet의 크기를 출력해준다.
