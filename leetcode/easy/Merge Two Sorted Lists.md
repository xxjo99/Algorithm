# leetcode - Merge Two Sorted Lists
leetcode 21. [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

## 코드
```java
class ListNode {
	int val;
	ListNode next;

	ListNode() {
	}

	ListNode(int val) {
		this.val = val;
	}

	ListNode(int val, ListNode next) {
		this.val = val;
		this.next = next;
	}
}

class Solution {
	public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
	   
		if (list1 == null) {
			return list2;
		} else if (list2 == null) {
			return list1;
		}
		
		ListNode result = new ListNode();
		
		ListNode node = result; 
		
		while (list1 != null && list2 != null) {
			
			if (list1.val < list2.val) {
				node.next = list1;
				list1 = list1.next;
			} else {
				node.next = list2;
				list2 = list2.next;
			}
			
			node = node.next;
			
		}
		
		node.next = list1 == null ? list2 : list1;
		return result.next;
	  
   }
}
```

## 풀이
주어진 연결리스트 두개를 오름차순으로 되어있는 하나의 연결리스트로 병합하는 문제. 연결리스트를 만드는 클래스는 주어져있다.

두 개의 리스트중 하나의 리스트가 null이라면 리스트는 정렬되어있는 상태이므로 null이 아닌 리스트를 반환해주면 된다.

결과값을 반환할 리스트 result와 값을 저장할 리스트 node를 생성한다. node에는 result를 연결해준다.

둘 중 하나의 리스트가 빌 때까지 반복해준다.

```java
while (list1 != null && list2 != null) {

  if (list1.val < list2.val) {
    node.next = list1;
    list1 = list1.next;
  } else {
    node.next = list2;
    list2 = list2.next;
  }

  node = node.next;

}

node.next = list1 == null ? list2 : list1;
```
둘 중 하나의 리스트가 빌 때까지 반복해준다.

리스트의 값이 더 작은 리스트먼저 node에 추가해준다.
추가해주었다면 node는 다음 노드에 값을 저장해야 하므로 다음 노드를 가리키도록 node.next로 초기화해준다.

while문이 끝나고 리스트에 남은 값이 남아있다면 남은 리스트를 node에 이어붙이고 result를 반환해주면 된다.
