## 1. let, const

### 기존 var
- 전통적으로 JavaScript는 함수 스코프와 전역 스코프만 지원해 변수의 생명주기와 접근을 제어했다.
- 선언된 블록 외부에서도 접근이 가능했기 때문에 수많은 버그의 원인이었다.
- 전역 변수를 남발할 가능성이 높고, 변수의 중복 선언이 가능했기 때문에 의도하지 않은 변수 값이 변경될 수 있다.
- 변수의 호이스팅으로 선언하기 전에 참조될 수 있다. 

### var vs let vs const

#### var 
- 블록 외부에서도 접근 가능
    ```js
    if (false) {
        var x = "hello";
    }

    console.log(x) // undefined 
    ```

    => let 키워드를 사용해 블록 스코프를 준수하는 변수를 선언한다.
    
- 함수 스코프
    ```js
    const age = 20;
    if (age > 19) {
        var txt = '성인';
    }
    console.log(txt); // 성인
    ```

    ```js
    function add(num1, num2) {
        var result = num1 + num2;
    }
    add (2+3);
    console.log(result) // ReferenceError - TDZ
    ```
    
    _=> 함수 내에 선언된 변수는 함수 밖을 못벗어남 !!_

#### let 
- 블록 스코프: 다른 블록에서 접근할 수 없다. (잠재적으로 위험한 부작용을 피할 수 있도록 오류 발생)
    ```js
    if (false) {
        let x = "hello";
    }
    console.log(x);  // ReferenceError: x is not defined
    ```

#### const

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
- 블록스코프


#### TDZ (Temporal Dead Zone)
- 초기화되지 않은 변수가 있는 곳
- 선언 전에 변수를 사용하는 것을 막기 위한 것
- let, const는 초기화되기 전에 사용할 수 없다.

_=> 예측 가능하고, 오류를 줄이기 위해 let, const를 지향!!_

## 2. Hoisting (호이스팅)
- 스코프 내부 어디서든 변수 선언이 최상위에 선언된 것처럼 동작하는 것
- 선언은 호이스팅되지만 할당은 호이스팅되지 않는다.

### 변수 생성 과정
- 선언 -> 초기화 -> 할당 과정으로 변수가 생성된다.

- var
    1. 선언 & 초기화 (undefined) 
    2. 할당
- let
    1. 선언: 호이스팅으로 선언
    2. 초기화: 코드에 도달할 때
    3. 할당
- const
    1. 선언 & 초기화 & 할당 (-> 값 변경이 안돼야 하기 때문에)


## 3. 화살표 함수
- 화살표 함수는 어휘 범위(lexical scope)로 바인드 된다. (화살표 함수 내부의 this는 부모 블록의 this와 같다.)
    
```js
function DelayedGreeter(name) {
    this.name = name;
}

DelayedGreeter.prototype.greet = function() {
    setTimeout(function cb() {
        console.log('Hello ' + this.name);
    }, 500);
};

const greeter = new DelayedGreeter('World');
greeter.greet(); // Hello undefined

```
- 콜백 함수(cb)의 범위와 greet 메소드의 범위가 다르기 때문에 제대로 작동하지 않는다.

```js
DelayedGreeter.prototype.greet = function() {
    setTimeout((function cb() {
        console.log('Hello ' + this.name);
    }).bind(this), 500);
};
```
- 이전에는 .bind() 함수를 통해 바인딩이 필요했다.

```js
DelayedGreeter.prototype.greet = function() {
    setTimeout(() => console.log('Hello' + this.name), 500);
};
```
- 화살표 함수로 코드가 짧아지고 직관적이게 된다.


## 4. 클래스 구문
- 내부적으로 객체 관리 방식(프로토타입을 통해 속성과 함수를 상속)이 바뀐것이 아니라 가독성이 좋고, 유용하게 구문 상 편의를 위한 것일 뿐이다.
- 기존 방식 사용
    ```js
    function Person(name, surname, age) {
        this.name = name;
        this.surname = surname;
        this.age = age;
    }

    Person.prototype.getFullName = function(0 {
        return this.name + ' ' + this.surname;
    })
    ```
- ES6 클래스 구문 사용
    ```js
    class Person {
        constructor (name, surname, age) {
            this.name = name;
            this.surname = surname;
            this.age = age;
        }

        getFullName () {
            return this.name + ' ' + this.surname;
        }
    }

<details>
<summary>참고</summary>

- [var vs let](https://www.youtube.com/watch?v=4_WLS9Lj6n4)

</details>