## 리액트 컴포넌트 라이프 사이클

- 컴포넌트의 수명은 보통 페이지에서 렌더링되기 전인 준비 과정에서 시작해 페이지에서 사라질 때 끝이 난다.

![image](https://user-images.githubusercontent.com/61968474/135211440-27584813-7ab9-4dfc-b279-7e9ec4dfbce0.png)

### 1. Initialization 
- 컴포넌트는 초기 state 및 props를 셋팅
### 2. Mounting 
- 컴포넌트가 브라우저 DOM에 mount할 준비가 됨
- constructor : 컴포넌트의 인스턴스를 새로 만들 때마다 생성자 메소드가 호출된다.
    ```jsx
    constructor(props) {
        super(props);
    }
    ```
- componentWillMount : React element를 실제 DOM 노드에 추가하기 직전에 호출되는 메소드, render가 호출되기 전이므로 setState를 사용해도 render가 호출되지 않는다.
- render : 화면에 표현된 JSX를 반환하고 화면에 그린다.
- componentDidMount : 컴포넌트가 화면에 모두 그려진 이후 호출된다. render가 호출된 후 호출되는 메소드

### 3. Updating 
- 새로운 props를 보내거나 state를 업데이트 해 컴포넌트를 업데이트
- shouldComponentUpdate
- render : 데이터가 변경되면 자동으로 호출되어 화면을 다시 그린다.
- componentDidUpdate : 화면이 다시 그려진 이후 호출된다.

### 4. Unmounting 
- 브라우저 DOM에서 component가 필요하지 않을 때 mount 해제
- componentWillUnmount : 컴포넌트가 화면에서 제거되기 전 호출된다.



### React v16.3 이후 변경된 부분

![image](https://user-images.githubusercontent.com/61968474/135213287-a4d29eab-2ce0-4248-af57-63ca8493be02.png)

- componentWillMount, componentWillReceiveProps, componentWillUpdate v17부터 사용 불가
- componentWillReceiveProps 대체 메소드 추가 getDerivedStateFromProps
- componentWillUpdate 대체 메소드 추가 getSnapshotBeforeUpdate
- componentDidCatch 컴포넌트 에러 핸들링 API 추가

참고
- [링크](https://velog.io/@kyusung/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EA%B5%90%EA%B3%BC%EC%84%9C-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%99%80-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%EC%9D%B4%EB%B2%A4%ED%8A%B8)