## Vector
- ArrayList와 같은 내부구조를 가지며, 크기가 가변적이다.
- Vector는 동기화된 메소드로 구성되어 있기 때문에 멀티 스레드가 동시에 이 메소드들을 실행할 수 없고, 하나의 스레드가 실행을 완료해야만 다른 스레드들이 실행할 수 있다.

### 장점
- 멀티 스레드 환경에서 안전하게 객체를 추가하고 삭제할 수 있다.

### 단점
- 스레드가 1개일 때에도 동기화하기 때문에 ArrayList보다 성능이 떨어진다.

```java
import java.util.Vector;

Vector vect = new Vector();
vect.add("one");
vect.add("two");
System.out.println(vect.get(0)); // one
```