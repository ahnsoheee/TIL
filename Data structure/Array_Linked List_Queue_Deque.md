## Array

![image](https://user-images.githubusercontent.com/61968474/94548701-12432780-028c-11eb-9b17-df2c44d24f55.png)

- 인덱스에 해당하는 원소를 빠르게 접근해야 할 때
- 데이터를 자주 바꾸거나 확인하는 일 없이 쌓아두고 싶을 때
- 데이터의 삽입/삭제가 빈번하다면 배열 사용은 비효율적
- 연산의 시간복잡도
  - a. i번째 원소 확인 : O(1) - 원소가 연속하게 배치되어 있기 때문

  - b. 원소를 끝에 추가 : O(1) - 배열의 길이를 알기 때문

  - c. 마지막 원소 제거 : O(1) - 배열의 길이를 알기 때문

  - d. 임의의 위치에 원소 추가 : O(N) - 원소 추가 후 전부 한 칸씩 뒤로 밀어야 함

  - e. 임의의 위치에 원소 제거 : O(N) - 원소 제거 후 전부 한 칸씩 앞으로 밀어야 함



## Linked-list (연결 리스트)

![image](https://user-images.githubusercontent.com/61968474/94561461-ff861e00-029e-11eb-92bd-7b0bef266e20.png)

- 각 원소가 자신의 다음 원소의 위치까지 가지고 있는 자료구조
- Singly Linked List : 자신의 다음 원소의 위치만 가지고 있는 연결리스트
- Doubly Linked List : 자신의 이전/다음 원소의 위치를 모두 가지고 있는 연결리스트
- Circular Linked List : 마지막 원소가 처음 원소의 위치를 가지고 있는 연결 리스트
- 삽입과 삭제 연산에 용이
- 시작 주소만 알고 있으면 연속된 데이터에 접근하기가 쉬움
- 탐색 속도가 단점
- 포인터의 사용으로 저장공간의 낭비를 초래할 수 있음
- 연산의 시간복잡도
  - a. 임의의 위치에 원소를 추가 : O(1) - 2개의 값만 바꾸면 됨

  - b. 임의의 위치의 원소를 제거 : O(1) - 2개의 값만 바꾸면 됨

  - c. 임의의 위치에 있는 원소 값 확인/ 변경 : O(N) - 해당 위치까지 가기 위해 이전의 모든 원소를 방문해야 함



## Queue (큐)

![image](https://user-images.githubusercontent.com/61968474/94561522-19bffc00-029f-11eb-91dc-dc0007fd8b80.png)

- 삽입과 삭제의 위치가 제한된 순서 리스트
- 삭제는 front에서만 이루어지고, 삽입은 rear에서만 이루어진다.
- 선입선출 구조 (FIFO : First - In - First - Out) : 가장 먼저 삽입된 원소가 가장 먼저 삭제된다.

## Deque (덱)

![image](https://user-images.githubusercontent.com/61968474/94561565-27758180-029f-11eb-84e1-64fb9a14d550.png)

- 양쪽 끝에서 삽입과 삭제가 모두 가능한 자료구조
- 큐의 확장형

- push_front() : front에 삽입 연산
- pop_front() : front에서 삭제 연산
- push_rear() : rear에 삽입 연산
- pop_rear() : rear에서 삭제 연산
