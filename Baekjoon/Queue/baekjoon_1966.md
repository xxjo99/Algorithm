# 백준 1966 - 프린터 큐
- https://www.acmicpc.net/problem/1966

## 코드
``` java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException { 
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		int t = Integer.parseInt(br.readLine());

		for (int test = 0; test < t; test++) {
			StringTokenizer st = new StringTokenizer(br.readLine(), " ");
			int n = Integer.parseInt(st.nextToken());
			int k = Integer.parseInt(st.nextToken());
			int count = 0;

			Queue<int[]> queue = new LinkedList<>();
			StringTokenizer st1 = new StringTokenizer(br.readLine(), " ");
			for (int i = 0; i < n; i++) {
				int a = Integer.parseInt(st1.nextToken());
				queue.add(new int[] { i, a });
			}

			while (!queue.isEmpty()) {
				int[] now = queue.poll();
				boolean able = true;
				
				for (int[] q : queue) {
					if (q[1] > now[1]) {
						able = false;
					}
				}

				if (able) {
					count++;
					if (now[0] == k) {
						break;
					}
				} else {
					queue.add(now);
				}
			}
			
			System.out.println(count);

		}
	}
}
```
