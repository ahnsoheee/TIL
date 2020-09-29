## 미들웨어

### 1. 애플리케이션 레벨 미들웨어
- app.use()
- app.METHOD() → app.post()
- 마운트 경로가 없는 미들웨어 함수는 앱이 요청을 수신할 때마다 실행된다.

```jsx
// 마운트되는 미들웨어
// /user/:id 경로에 대한 모든 유형의 HTTP 요청에 대해 실행된다.
app.use('/user/:id', function (req, res, next) {
  console.log('Request Type:', req.method);
  next();
});

// 
app.get('/user/:id', function (req, res, next) {
  res.send('USER');
});
```

### 2. 라우터 레벨 미들웨어
- router.use() 및 router.METHOD()
- express.Router() 인스턴스에 바인드된다는 점을 제외하면 애플리케이션 레벨의 미들웨어와 동일한 방식으로 동작한다.

### 3. 오류 처리 미들웨어

```jsx
// 4개의 인가 필요하다. 
// next를 사용할 필요는 없지만, 지정하지 않으면 일반적인 미들웨어로 해석되어 오류 처리에 실패한다.
  app.use(function(err, req, res, next) {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

## 라우팅

- 애플리케이션 엔드 포인트 (URI)의 정의와 URI가 클라이언트 요청에 응답하는 방식
- 라우트 메소드 : HTTP 메소드 중 하나로부터 파생되며, Express 클래스의 인스턴스에 연결된다.

```jsx
// GET method route
app.get('/', function (req, res) {
  res.send('GET request to the homepage');
});

// POST method route
app.post('/', function (req, res) {
  res.send('POST request to the homepage');
});
// all : 어떠한 HTTP 메소드로부터도 파생되지 않으며, 
// 모든 요청 메소드에 대해 한 경로에서 미들웨어 함수를 로드하는 데 사용
app.all('/secret', function (req, res, next) {
  console.log('Accessing the secret section ...');
  next(); // pass control to the next handler
});
```

- 라우트 경로 : 문자열 / 문자열 패턴 / 정규식
- 라우트 핸들러 : 미들웨어와 비슷하게 동작하는 여러 콜백 함수를 제공하여 요청을 처리한다.

## app.route()

- 라우트 경로에 대해 체인 가능한 라우트 핸들러 작성 가능
- 모듈식 라우트를 작성하면 중복을 줄일 수 있다.

## espress.Router()

- 모듈식 마운팅 가능한 핸들러 작성 가능
- Router 인스턴스는 완전한 미들웨어이자 라우팅 시스템
