## 동기 vs 비동기 & Blocking vs Non-blocking
#### 동기
- 어떤 요청과 응답이 동시에 이루어지기 때문에 결과가 주어질 때까지 다른 작업을 수행할 수 없는 방식
- 직렬적으로 작업을 수행한다.
- 요청을 하는 시기와 응답을 받는 시기가 일치한다.

![image](https://user-images.githubusercontent.com/61968474/136347366-f53753bf-107b-4e55-a7c1-efcf729cc66a.png)


####  비동기 
- 요청과 응답이 동시에 이루어지지 않고 따로 이루어지는 것

- 응답이 올 때까지 기다리더라도 다른 작업을 할 수 있어 자원을 효율적으로 활용할 수 있다.

![image](https://user-images.githubusercontent.com/61968474/136347432-1122db14-f898-4a52-9062-182edf80c0ef.png)

**=> 동기 vs 비동기 : 처리해야 할 작업을 어떤 흐름으로 처리할 것인가에 대한 관점으로 구분된 것**

## Blocking vs Non-blocking

#### Blocking

- 어떤 요청에 대한 응답이 올 때까지 대기하는 것

- 동기적인 수행을 위해서는 blocking 되어야 한다.

-> 호출된 함수가 자신의 작업을 마칠 때까지 제어권을 넘겨주지 않는 방식


#### Non-blocking

- 어떤 요청에 대한 응답을 기다리지 않고 계속 루틴을 실행하는 것

-> 호출된 함수가 바로 제어권을 넘겨줘서 다음 작업을 수행할 수 있는 방식

- 비동기를 위해서는 non-blocking 되어야 하지만 non-blocking 방식이 비동기는 아님

**=> blocking vs non-blocking : 처리되어야하는 작업이 전체적인 작업의 흐름을 막느냐 안막느냐에 대한 관점**


