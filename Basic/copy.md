## Copy

### 얕은 복사 (Shallow copy)
- 객체를 복사할 때 복사된 값은 원래 값의 참조 값(객체의 주소)을 가리키고 있기 때문에 복사된 객체나 원본 객체 중 값이 변하면 둘 다 변한다.
- 일반적으로 '='을 이용해 복사하는 경우 primitive 값이 아닌 값은 얕은 복사에 해당된다.
- primitive 값은 참조값이 아니라 값이 복사된다.

    ```js
    const arr1 = [1, 2, 3]
    const arr2 = arr1
    ```
- spread (...obj)
    ```js
    const obj = {
    a: 1,
    b: {
        c: 2,
    },
    };

    const copiedObj = {...obj}

    copiedObj.b.c = 3

    obj.b.c === copiedObj.b.c // true
    ```
###

### 깊은 복사 (Deep copy)
- 새로운 주소를 할당받는 것
- 깊은 복사된 객체는 원본과의 참조가 완전히 끊어진 객체이다.
- 원본 객체와 복사된 객체는 독립적이다.
- 한 객체의 값이 바뀌더라도 서로 영향을 미치지 않는다.
- JSON.parse(JSON.stringify(obj) : 배열 관련 함수는 사용 불가능하다. Date 객체를 string으로 변환한다. 다른 방법에 비해 속도가 매우 느리다.
- bind() 함수까지 복사

    ```js
    const obj = {
    a: 1,
    b: {
        c: 2,
    },
    };

    const copiedObj = JSON.parse(JSON.stringify(obj));

    copiedObj.b.c = 3

    obj.b.c === copiedObj.b.c //false
    ```