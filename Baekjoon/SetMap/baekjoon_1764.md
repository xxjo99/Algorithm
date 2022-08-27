# 백준 1764 - 듣보잡
- https://www.acmicpc.net/problem/1764

## 코드
``` java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.HashSet;
import java.util.StringTokenizer;

public class Main {
	
	public static void main(String[] args) throws IOException {
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		StringTokenizer st = new StringTokenizer(br.readLine(), " ");
		int n = Integer.parseInt(st.nextToken());
		int m = Integer.parseInt(st.nextToken());
		
		HashSet<String> set = new HashSet<>();
        for (int i = 0; i < n; i++) {
            set.add(br.readLine());
        }
		
        ArrayList<String> list = new ArrayList<>(); 
        for (int i = 0; i < m; i++) {
            String s = br.readLine();
            
            if (set.contains(s)) {
            	list.add(s);
            }
        }
        
        Collections.sort(list);
        System.out.println(list.size());
        for (String s : list) {
            System.out.println(s);
        }
        
	}

}

```

## 풀이
HashSet을 생성하고 듣도 못한 사람을 저장한다

ArrayList를 만들고 m번 반복하면서 보도못한사람을 입력받아 HashSet과 비교하면서 포함되있다면 ArrayList에 저장한다.

마지막으로 ArrayList의 크기와 포함된 데이터를 출력해주면 된다.
