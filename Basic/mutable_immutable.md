## Mutable vs Immutable

### mutable
- 변할 수 있다는 의미로 해당 데이터의 주소를 참조한다.
- List, Dictionary, HashMap, ArrayList 
- object 타입의 a를 =을 이용해 b로 복사하고 a의 값을 변경한다면 b도 변경된다. 
    -> 같은 주소를 가리키고 있기 때문에 해당 값을 사용하는 모든 곳에서 사이드 이펙트가 발생할 수 있다.

### Immutable
- 변할 수 없는 값을 의미
- 해당 데이터 주소와 별개의 주소를 할당받는다.
- String, Number
- 숫자 타입의 변수 a를 =을 이용해 b에 할당해 주는 경우 a의 값을 변경해도 b에는 아무 영향이 없다. -> a와 b는 서로 다른 주소를 가리키기 때문이다.

