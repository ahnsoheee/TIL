## Promise
- 비동기 작업의 최종 결과를 나타낸다.
- 대기중(pending) : 아직 비동기 작업이 완료되지 않은 것
- 이행됨(fulfilled) : 비동기 작업이 성공적으로 끝난 것
- 거부됨(rejected) : 작업이 실패해 종료된 것
- promise가 이행되거나 거부되면 처리된(settled)것으로 간주된다.
- 이행 값이나 거부와 관련된 오류(원인)를 받으려면 Promise의 then() 메소드를 사용한다.
```js
promise.then([onFulfilled], [onRejected])
```
- onFulfilled()는 최종적으로 promise의 이행 값을 받는 함수이고, onRejected()는 거부 이유(있을 경우)를 받는다.

### then
- then() 메소드는 동기식으로 다른 프로미스를 반환한다.
- onFulfilled() / onRejected() 함수 중 하나가 x라는 값을 반환할 경우
    - x가 값이면 이행 값 x를 가지고 핸들러가 호출된다.
    - x가 프로미스거나 thenable(then() 메소드가 존재)인 경우, x를 가지고 핸들러가 호출되거나 x의 거부 이유로 에러 핸들러가 호출된다.
- onFulfileld() / onRejected() 핸들러를 지정하지 않으면 이행 값/거부 이유가 자동으로 체인 내 프로미스들로 전달된다.
    - ex) onRejected() 핸들러로 catch될 때 까지 전체 체인에 오류를 자동으로 전파할 수 있다.

```js
asyncOperation(arg) {
    .then(result1 => {
        // 다른 프로미스를 반환
        return asyncOperation(arg2);
    })
    .then(result2 => {
        // 값을 반환
        return 'done';
    })
    .then(undefined, err => {
        // 체인의 모든 에러를 여기서 처리
    })
}
```
### ES2015 Promise에 의해 제공되는 API

#### 생성자(new Promise (function (resolve, reject) {}))
- 인자로 전달된 함수의 동작을 기반으로 이행하거나 거부하는 새로운 프로미스를 만든다.
- resolve(obj) : 값이 thenable(then() 메소드를 가진 객체)인 경우 반환된 프로미스는 then 메소드를 처리하고 마지막 상태를 취한다. 그렇지 않은 경우 반환된 프로미스는 주어진 값으로 이행한다.
- reject(err) : err을 이유로 프로미스를 거부한다. 

#### Promise 객체의 정적 메소드
- Promise.resolve(obj): thenable이나 값으로 새로운 프로미스를 생성한다.
- Promise.reject(err) : 주어진 이유로 거부되는 프로미스 객체를 만든다.
- Promise.all(iterble) : 반복 가능한 객체의 모든 항목들이 이행되고 나면 모든 이행 값들을 가지고 이행하는 프로미스를 생성하는데, 하나의 항목이라도 거부될 경우 첫 번째 거절 이유를 가지고 거절된다. 
- Promise.race(iterable) : 반복 가능한 객체 내에 있는 프로미스들 중 가장 먼저 이행되거나 거절된 결과를 가지고 이행되거나 거부되는 프로미스를 반환한다.
