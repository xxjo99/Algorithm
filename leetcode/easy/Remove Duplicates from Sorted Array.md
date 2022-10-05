# leetcode - Remove Duplicates from Sorted Array
leetcode 26. [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## 코드
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int idx = 1;

        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] != nums[i + 1]) {
                nums[idx] = nums[i + 1];
                idx++;
            }
        }

        return idx;
    }
}
```

## 풀이
주어진 오름차순 배열의 중복된 수를 제거하는 문제.

먼저 처음 idx값을 1로 설정한다.

반복문을 돌면서 nums[i]와 nums[i+1] 값이 달라진다면 값이 달라졌다는 뜻이므로 nums[idx]에 nums[i+1]로 새로운 값을 넣어주고 idx를 1 증가시켜준다.

반복문이 끝나면 idx를 return 해주면 된다.

