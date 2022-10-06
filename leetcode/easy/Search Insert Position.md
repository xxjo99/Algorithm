# leetcode - Search Insert Position
leetcode 35. [Search Insert Position](https://leetcode.com/problems/search-insert-position/)

## 코드
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int start = 0;
        int end = nums.length - 1;
        
        while(start <= end) {
            int mid = start + end / 2;

            if(nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }

        return start

    }
}
```

## 풀이
정수형 배열 nums와 찾는 수 target가 주어질때 nums에서 target를 찾는 문제. target이 없다면 target가 있어야하는 위치의 index를 반환한다.

이진탐색을 사용하면 O(log₂n)의 시간복잡도로 해결할 수 있다.

``` java
int start = 0;
int end = nums.length - 1;
```
이진탐색을 위한 변수를 생성한다 각각 배열의 시작과 끝을 나타낸다.

```java
while(start <= end) {
    int mid = start + end / 2;

    if(nums[mid] == target) {
        return mid;
    } else if (nums[mid] < target) {
        start = mid + 1;
    } else {
        end = mid - 1;
    }
}
return start
```
start가 end보다 작거나 같을경우 계속 반복하면서 확인해준다.

먼저 중앙값을 나타내는 변수 mid를 생성하고 중앙값을 구해 넣어준다.

그리고 mid와 target가 같은지 작은지 큰지 판별해 나머지 반을 버리고 다시 반복해준다. target를 찾았다면 mid를 반환해주면 된다.

그렇지않고 배열에 target가 없다면 start를 반환해주면 된다.


