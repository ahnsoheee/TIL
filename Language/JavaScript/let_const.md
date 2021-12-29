## let, const

### 기존 var
- 전통적으로 JavaScript는 함수 스코프와 전역 스코프만 지원해 변수의 생명주기와 접근을 제어했다.
- 선언된 블록 외부에서도 접근이 가능했기 때문에 수많은 버그의 원인이었다.
- 전역 변수를 남발할 가능성이 높고, 변수의 중복 선언이 가능했기 때문에 의도하지 않은 변수 값이 변경될 수 있다.
- 변수의 호이스팅으로 선언하기 전에 참조될 수 있다.

### var vs let

#### var 
- 블록 외부에서도 접근 가능
    ```js
    if (false) {
        var x = "hello";
    }

    console.log(x) // undefined 
    ```

    => let 키워드를 사용해 블록 스코프를 준수하는 변수를 선언한다.

#### let 
- 다른 블록에서 접근할 수 없다. (잠재적으로 위험한 부작용을 피할 수 있도록 오류 발생)
    ```js
    if (false) {
        let x = "hello";
    }
    console.log(x);  // ReferenceError: x is not defined
    ```

### const

```js
const x = "This will never change";
x = "...";

// TypeError: Assignment to constant variable
```
- 다른 언어의 상수 값과 다른 방식으로 동작
- const는 할당된 값이 상수가 되는 것이 아니라 바인딩된 값이 상수가 된다.
    ```js
    const x = {};
    x.name = "John";
    ```
- 객체 내부의 속성을 변경하면 실제 값이 변경되지만 변수와 객체 사이의 바인딩은 변경되지 않기 때문에 오류가 발생하지 않는다.
- 반대로 전체 변수를 재할당하면 변수와 값 사이의 바인딩이 변경되어 오류가 발생한다.
- 코드 내 스칼라 값이 실수로 변경되지 않도록 보호하거나, 다른 곳에서 실수로 재할당하지 않도록 하기 위해 const를 사용한다.
- 모듈을 사용할 때 모듈이 가진 변수가 재할당되지 않도록 const를 사용한다.
