## Python 데이터 구조 

### Stack (스택)
- 나중에 넣은 데이터를 먼저 반환하도록 설계된 메모리 구조
- Last In First Out
- 데이터의 입력을 push → append(), 출력을 pop()


### Queue (큐)
- 먼저 넣은 데이터를 먼저 반환하도록 설계된 메모리 구조
- First In First Out
- 스택과 반대 개념
- 파이썬은 리스트를 사용해 큐 구조를 사용
- 파이썬은 리스트를 사용해 큐 구조를 사용
put → append(), get → pop(0)


### Tuple (튜플)
- 값의 변경이 불가능한 리스트
- 선언 시 "( )" 사용
- 리스트의 연산, 인덱싱, 슬라이싱 등 동일하게 사용
- 프로그램을 작동하는 동안 변경되지 않은 데이터의 저장
- 함수의 반환 값 등 사용자의 실수에 의한 에러를 사전에 방지


### 집합 (Set)
- 값을 순서없이 저장, 중복을 불허하는 자료형
- 수학에서 활용하는 다양한 집합연산 가능 → 교집합 : intersection(), 차집합 : difference(), 합집합 : union()
```python
a = set([1, 2, 3])
b = {1, 2, 3, 4, 5}
```


### Dictionary (사전)
- 데이터를 저장할 때는 구분지을 수 있는 값을 함께 저장
- 구분을 위한 데이터 고유 값을 Identifier 또는 Key 라고 함
- Key 값을 활용해 데이터 값(Value) 관리
- key와 value를 매칭 해 key로 value를 검색
- 다른 언어에서는 Hash table이라는 용어로 사용
- {key1: value1, key2: value2, key3: value3 ...} 형태
- dict.items() : 튜플 형태로 키와 값이 출력
```python
for key, value in country_code.items(): // 언팩킹 
	print('key : ', key) 
	print('value : ', value)
```
- dict.keys() : 키 값만 출력
- dict.values() : value만 출력


### collections
- List, Tuple, Dict에 대한 Python Built-in 확장 자료 구조(모듈)
- 편의성, 실행 효율 등을 사용자에게 제공
```python
from collections import deque 
from collections import Counter 
from collections import OrderedDict 
from collections import defaultdict 
from collections import namedtuple
```


### deque
- 스택과 큐를 지원하는 모듈
- 리스트에 비해 빠르고 효율적인 자료 저장 방식을 지원
- rotate, reverse 등 Linked List의 특성을 지원
- appendleft(), extend(), extendleft() : 앞에 역순으로 추가
- 기존 리스트 보다 효율적 메모리 구조로 처리 속도 향상


### OrderedDict
- Dictionary와 달리 데이터를 입력한 순서대로 dict를 반환

    → python 3.6부터 dict도 입력한 순서를 보장해서 출력
- Dict type의 값을 value 또는 key 값으로 정렬할 때 사용 가능
```python
for k, v in OrderedDict(sorted(d.items(), key=lambda t: t[0])).items() 
	print(k, v)
```

### defaultdict
- Dict type의 값에 기본 값을 지정, 신규 값 생성 시 사용하는 방법
- 텍스트 마이닝 접근법 - Vector Space Model
```python
from collections import defaultdict 

d = defaultdict(lambda : 0) // default value = 0 
d['first'] // => 0
```

### Counter
- 시퀀스 타입의 데이터 요소들의 갯수를 dict 형태로 반환
- Set 연산 지원 : +, -, &, |
```python
c = Counter(['b', 's', 's', 's', 'b']) 
print(c) 
// {'b': 2, 's': 3} 

c = Counter({'red': 4, 'blue': 2}) 
print(list(c.elements())) 
// [ 'red', 'red', 'red', 'red', 'blue', 'blue']

c = Counter(cat = 2, dog = 3) 
print(list(c.elements())) 
// ['cat', 'cat', 'dog', 'dog', 'dog']
```

### namedtuple
- 튜플 형태로 데이터 구조체를 저장하는 방법
- 저장되는 데이터의 variable을 사전에 지정해서 저장
```python
from collections import namedtuple

Point = namedtuple('Point', [x, y]) 
p = Point(11, y=22) 
p[0], p[1] // (11, 22)

x, y = p 
print(x, y) // 11 22 
print(p.x + p.y) // 33 
print(Point(x=11, y=22)) // Point(x=11, y=22)
```