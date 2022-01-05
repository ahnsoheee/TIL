## 클로저 (Closure)

![Node js-6 2](https://user-images.githubusercontent.com/61968474/148192335-756f015b-783b-4320-bba8-e58ce1dc9749.jpg)

- 함수 밖에서 선언된 변수를 함수 내부에서 사용할 때 클로저가 생겨난다고 할 수 있다.
```js
function getClosure() {
		var text= 'variable1';
		return function() {
			return text;
		};
}
var closure= getClosure();
console.log(closure()); // Closure
```

- 클로저를 은닉화에 사용할 수 있다.
```js
function counter() {
    let count = 0; // 은닉화

    return function() {
        return count++;
    }
}

let counter = counter();

console.log(counter()); // 0
console.log(counter()); // 1
console.log(counter()); // 2
```

- 함수가 소멸될 때까지 변수가 메모리에 남아있기 때문에 잘못 사용하면 성능과 메모리 문제가 발생할 수 있다.

### 클로저의 생성 조건
- 클로저를 이용할 때 외부함수의 지역변수 값이어야 한다.
- 내부 함수가 익명 함수로써 외부 함수의 return 값으로 사용되어야 한다.
- 반환되는 내부함수는 외부 함수의 실행환경에서 실행되어야 한다.