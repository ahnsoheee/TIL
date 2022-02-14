## HashMap

- [Hash Table 자료구조](https://github.com/ahnsoheee/TIL/blob/master/Data%20structure/HashTable.md)

### HashMap의 함수
- put(key, value) : key와 value를 해시맵에 추가한다.
- getValue(key) : 입력받은 key의 value를 반환한다.
- keys() : 해시맵의 모든 key를 반환한다.
- remove(key) : 입력받은 key와 key에 해당하는 value를 삭제한다.
- replace(key, value) : 입력받은 key의 value를 입력받은 value로 변경한다.
- size() : 해시맵의 value의 갯수를 반환한다.
- isEmpty() : 해시맵의 데이터가 0인지 확인한다.
- clear() : HashMap의 모든 데이터를 삭제한다.
- contains() : 입력받은 key가 HashMap에 있는지 확인한다.

## Map vs HashMap vs HashTableMap vs TreeMap

![image](https://user-images.githubusercontent.com/61968474/94562262-1416e600-02a0-11eb-89a1-1875ac7626f3.png)

- Map은 인터페이스이다. 인터페이스는 선언만 가능하고 객체 생성이 불가능하다.
- HashMap은 Map의 자식 클래스로 Map의 메소드를 상속받는다.

```java
Map<String, String> map = new HashMap<>(); 
// or
HashMap<String, String> hashMap = new HashMap<>();

```

### 1. Map
- red-black tree 사용
- 최악의 경우 시간복잡도 : O(n) - 모든 데이터를 탐색
- 최상의 경우 시간복잡도 : O(logn)
- HashMap을 위한 인터페이스: 특정한 Map을 사용하기 위해 인터페이스를 사용
- new Map()을 사용하면 일일이 내부 알고리즘을 구현해야 한다.
- 중복을 허용하지 않고, key-value 쌍으로 이루어진다.
- key와 value는 null을 허용한다.

### 2. HashMap
- hash함수가 사용된 Map: 해시 값을 생성한다.
- 이상적으로는 O(1) 시간 복잡도를 갖지만 실제로는 O(n)을 소요한다.
- 삽입과 제거의 과정이 가볍다.
- key나 value에 null값 저장 가능

### 3. HashTableMap
- key와 value는 null을 허용하지 않는다.

### 4. TreeMap
- SortedMap을 상속받고, key에 대해 정렬되어있다.