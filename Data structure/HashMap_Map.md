## 해시맵 (HashMap)

![image](https://user-images.githubusercontent.com/61968474/94562227-082b2400-02a0-11eb-9663-35fa44330fbe.png)

- hash 함수를 통해 key를 해시 값으로 변환하여 value에 접근한다.
- hash function : 해시 코드로 변환하는 함수
- put(key, value) : key와 value를 해시맵에 추가한다.
- getValue(key) : 입력받은 key의 value를 반환한다.
- keys() : 해시맵의 모든 key를 반환한다.
- remove(key) : 입력받은 key와 key에 해당하는 value를 삭제한다.
- replace(key, value) : 입력받은 key의 value를 입력받은 value로 변경한다.
- size() : 해시맵의 value의 갯수를 반환한다.
- isEmpty() : 해시맵의 데이터가 0인지 확인한다.
- clear() : HashMap의 모든 데이터를 삭제한다.
- contains() : 입력받은 key가 HashMap에 있는지 확인한다.


## Map과 HashMap의 차이

![image](https://user-images.githubusercontent.com/61968474/94562262-1416e600-02a0-11eb-89a1-1875ac7626f3.png)

  1) Map
  - red-black tree 알고리즘 사용
  - 최악의 경우 시간복잡도 : O(n) - 모든 데이터를 탐색
  - 최상의 경우 시간복잡도 : O(logn)
  - HashMap을 위한 인터페이스 - 특정한 Map을 사용하기 위해 인터페이스를 사용
  - new Map()을 사용하면 일일이 내부 알고리즘을 구현해야 한다.

  2) HashMap
  - hash함수가 사용된 Map - 해시 값을 생성한다.
  - 이상적으로는 O(1) 시간 복잡도를 갖지만 실제로는 O(n)을 소요한다.
  - 삽입과 제거의 과정이 가볍다.
  - key나 value에 null값 저장 가능

## Hash Function

1) 나눗셈 법

- h(k) = k mod m
- 입력받은 key의 각 문자를 유니코드로 변환 후 HashMap의 size로 나눈 나머지 값으로 사용한다.
- m은 HashMap의 크기이며 소수를 사용한다. (2의 제곱수와 거리가 먼 소수)

2) 곱셈 법

- h(k) = (kA mod 1) * m
- k는 숫자로 된 키, 0 < A < 1
- m은 중요하지 않으며 보통 2의 제곱 수로 정한다.
- 나눗셈 법보다는 느리고 2진수 연산에 최적화된 컴퓨터 구조를 고려한 해시함수이다.

3) Universal Hashing

- 다수의 해시 함수를 만들고 이 해시함수의 집합에서 무작위로 해시함수를 선택해 해시값을 만드는 기법
- 무작위로 뽑은 해시함수가 주어졌을 때 임의의 키 값을 임의의 해시값에 매핑할 확률을 1/m으로 만드는 것이 목적이다.

4) MD5 (Message - Digest Algorithm)

- 임의의 길이의 값을 입력받아 128 비트 길이의 해시값을 출력하는 알고리즘
- 같은 입력값이면 항상 같은 출력값이 나오고, 서로 다른 입력값에서 같은 출력값이 나올 확률은 극히 낮다.
- 단방향 암호화이기 때문에 해시값을 복호화는 할 수 없다.

5) SHA (Secure Hash Algorithm)

- 미국 국립표준기술연구소에서 표준으로 채택한 암호학적 해시 함수
- 해시 길이에 따라 SHA-256, SHA-384, SHA-512 비트를 선택해 사용할 수 있으며, 해시 길이가 길수록 안전하다

6) Chaining 

![image](https://user-images.githubusercontent.com/61968474/94562313-22fd9880-02a0-11eb-9aa3-5b95a8869d7c.png)

- 데이터가 많으면 충돌이 발생하게 되어 충돌을 방지하는 방법이다.

  a) Separate Chaining 

  - 한 버킷 당 들어갈 수 있는 엔트리의 수에 제한을 두지 않는 방법
  - 연결 리스트를 사용한다.
  - 충돌이 발생하면 그 인덱스가 가리키는 연결리스트에 노드를 추가하여 값을 추가한다.

  b) Linear Probing

  - 충돌이 발생했을 떄, index 뒤에 있는 버킷 중 빈 버킷을 찾아 값을 저장한다.
