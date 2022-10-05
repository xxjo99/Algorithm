# leetcode - Remove Element
9. [Remove Element](https://leetcode.com/problems/remove-element/)

## 코드
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int idx = 0;;

        for (int i = 0; i < nums.length; i++) {

            if (nums[i] != val) {
                nums[idx] = nums[i];
                idx++;
            }

        }

        return idx;
    }
}
```

## 풀이
주어진 배열에서 제시된 숫자를 모두 제거하고 배열의 길이와 변환된 배열을 반환하는 문제. 배열은 직접 변환시킨다.

최종 배열의 길이와 인덱스를 나타내는 변수 idx를 초기값 0으로 생성한다.

반복문을 돌면서 제거할 숫자와 다르다면 nums배열의 idx에 nums[i]를 넣어주고 idx를 1 증가시켜주면된다.

반복문이 끝났다면 idx를 반환한다.

