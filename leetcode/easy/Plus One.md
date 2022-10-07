# leetcode - Plus One
leetcode 66. [Plus One](https://leetcode.com/problems/plus-one/)

## 코드
```java
public class PlusOne {

    public int[] plusOne(int[] digits){

        int plus = 1;
        int index = digits.length - 1;

        while(index >= 0 && plus > 0){
            digits[index] = (digits[index] + 1) % 10;
            plus = (digits[index] == 0)? 1 : 0;

            index--;
        }

        if(plus > 0) {
            digits = new int[digits.length + 1];
            digits[0] = 1;
        }

        return digits;
    }
}
```

## 풀이
주어진 배열의 원소들을 하나로 생각하고 1을 더한 결과를 구하는 문제

먼저 주어진 배열의 맨 뒤에 1을 더하고 1의 자리수만 저장한다.

저장한 수가 0일 경우 올림이 발생한 뜻이므로 plus를 1로 설정하고 반복해준다.

저장한 수가 0이 아닐경우 올림되는 수는 0이므로 덧셈과정이 끝났다는 뜻이므로 반복문을 끝낸다.

반복을 완료했을때 plus가 1일 경우 주어진 수보다 한자리가 더 많다는 뜻이므로 새로운 배열을 생성하고 첫번째 인덱스를 1로 설정하고 반환해주면 된다.




