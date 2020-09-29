## 구성
    - URI, HTTP METHOD, 표현
    
## 클라이언트 - 서버 구조
- 서버는 API 제공
- 클라이언트는 사용자 인증이나 컨텍스트(세션, 로그인 정보) 등을 직접 관리하는 구조
  → 클라이언트와 서버간의 의존성이 줄어든다.
    
## HTTP METHOD
- POST : 해당 URI를 요청하면 리소스를 생성한다.
- GET : 해당 리소스를 조회, 리소스를 조회하고 해당 도큐먼트의 자세한 정보를 가져온다.
- PUT : 해당 리소스를 수정한다.
- DELETE : 리소스를 삭제한다.
    
## URI 설계 시 주의할 점
- '/' 구분자는 계층 관계를 나타내는데 사용한다.
- URI 마지막 문자로 '/'를 포함하지 않는다.

```jsx
http://restapi.example.com/houses/apartments/ (X)
http://restapi.example.com/houses/apartments  (0)
```

- '-'는 URI 가독성을 높이는데 사용
- '_'은 URI에 사용하지 않는다.
- URI 경로에는 소문자가 적합하다.
- 파일 확장자는 URI에 포함시키지 않는다.
