
## Queue (큐)

![image](https://user-images.githubusercontent.com/61968474/94561522-19bffc00-029f-11eb-91dc-dc0007fd8b80.png)

#### 특징

- 삽입과 삭제의 위치가 제한된 순서 리스트
- 삭제는 front에서만 이루어지고, 삽입은 rear에서만 이루어진다.
- 선입선출 구조 (FIFO : First - In - First - Out) : 가장 먼저 삽입된 원소가 가장 먼저 삭제된다.

#### 시간 복잡도

- 삽입 / 삭제 : O(1)

## Deque (덱)

![image](https://user-images.githubusercontent.com/61968474/94561565-27758180-029f-11eb-84e1-64fb9a14d550.png)

#### 특징

- 양쪽 끝에서 삽입과 삭제가 모두 가능한 자료구조
- 큐의 확장형

#### 시간 복잡도

- 원소를 앞/뒤에서 삽입/삭제 : O(1)
- 탐색 : O(1) - index로 접근

#### 연산

- push_front() : front에 삽입 연산
- pop_front() : front에서 삭제 연산
- push_rear() : rear에 삽입 연산
- pop_rear() : rear에서 삭제 연산
