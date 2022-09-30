# leetcode - Two Sum
- https://leetcode.com/problems/two-sum/

## 코드
```java
class Solution {
	public int[] twoSum(int[] nums, int target) {
		Map<Integer, Integer> map = new HashMap<>();
		
		for (int i = 0; i < nums.length; i++) {
			if (map.containsKey(nums[i])) {
				return new int[] { 
          map.get(nums[i]), i
        };
			}
			
			map.put(target - nums[i], i);
		}
		
		return new int[] {};
	}
}
```

## 풀이
주어진 배열에서 두 수의 합이 target이 되는 배열의 인덱스값을 찾는 문제 

이중반복문을 사용해서 해결할 수 있지만 시간복잡도가 O(n^2) 이지만 Map을 사용하면 O(n)으로 Map를 사용해 푸는게 효율적이다.

먼저 Integer, Integer 형태의 Map을 선언해주고, 반복문을 돌아준다.

Map에는 targer-nums[i], index를 저장해준다.

그리고 map.containsKey(nums[i])가 참이라면 현재의 값과 더해서 target이 되는 값이 존재한다는 뜻이다.

그러므로 map에 key값으로 저장된 nums[i]의 인덱스와 현재 인덱스를 저장해 출력해주면 된다
