## Prototype

- JavaScript는 클래스라는 개념이 없고 프로토타입을 사용한다. (ES6에서 클래서 문법이 등장)
- 기존의 객체를 복사해서 새로운 객체를 생성하는 프로토타입 기반의 언어이다.

    ![image](https://user-images.githubusercontent.com/61968474/134460594-969f55d6-ec09-48d7-8be5-48cd2271dcfd.png)

- 생성자 함수로 생성된 객체가 공통으로 가지는 공간
- 메소드를 하나만 생성해도 모든 객체가 해당 메소드를 사용할 수 있다.
- 동일한 함수 생성에 따른 비효율적인 메모리 이용을 해결할 수 있다.
- 자바스크립트의 모든 함수는 변수 prototype을 갖는다.
- prototype은 객체다.

    ```js
    function Person() {
        this.name = 'Kim'
        this.age = 19
    }
    Person.prototype.getName = function() {
        return this.name;
    }
    ```

### \_proto_ & constructor & prototype
![image](https://user-images.githubusercontent.com/61968474/134461416-a96440ec-38c9-4dba-b656-5b8b314932ce.png)

- \_proto_: 자신을 만들어낸 객체의 원형과 연결된 속성
- constructor: 생성자, 자신을 만들어낸 객체와 연결된 속성
- prototype: 자신을 원형으로 만들어진 새로운 객체들과 연결된 속성