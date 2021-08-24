## Redux

![image](https://user-images.githubusercontent.com/61968474/130623375-aa7f69b7-64bb-4c58-a0e1-79cd22e5a52f.png)

- 상태 관리 라이브러리
- 컴포넌트의 상태관련 로직을 분리해서 사용할 수 있다.
- 액션에 대한 처리 로직을 정의하고, 해당 액션이 발생하면 로직을 수행하고 스토어에 반영한다.
- 컴포넌트 간의 상태를 공유할 수 있다.

#### 기본 개념
- useSelctor : 스토어에 상태값을 가져올 수 있다.
- useDispatch : 액션을 발생시킬 수 있다.
- reducer : 상태의 변화를 일으키는 함수를 말한다.

#### 3가지 원칙
1. Single Source of Truth
- 단 하나의 스토어를 사용하며, 이 안에 모든 상태 값들이 포함되어있다.

2. State is Read-only
- 스토어 내 모든 state 값은 읽기 전용이기 때문에 컴포넌트에서 직접 state 값을 수정할 수 없다.
- state를 수정하기 위해서는 action을 발생시켜 변경해야 한다.

3. Changes are made with pure functions
- reducer는 이전 상태와 액션을 받아 다음 상태를 반환하는 순수 함수이다.
- 순수 함수로 작성되어야 하며, 순수하지 않은 API 호출을 하지 말아야 한다.

#### 예제
1. Reducer

```JavaScript
function counterReducer(state = initialState, action) {
  // Reducers usually look at the type of action that happened
  // to decide how to update the state
  switch (action.type) {
    case 'counter/incremented':
      return { ...state, value: state.value + 1 }
    case 'counter/decremented':
      return { ...state, value: state.value - 1 }
    default:
      // If the reducer doesn't care about this action type,
      // return the existing state unchanged
      return state
  }
}
```

2. Store
```JavaScript
const store = Redux.createStore(counterReducer)
```

3. Dispatching Actions
```JavaScript
document.getElementById('increment').addEventListener('click', function () {
  store.dispatch({ type: 'counter/incremented' })
})

document.getElementById('decrement').addEventListener('click', function () {
  store.dispatch({ type: 'counter/decremented' })
})
```

[참고](https://redux.js.org/tutorials/fundamentals/part-1-overview)