## URI / URL / URN

![image](https://user-images.githubusercontent.com/61968474/130655307-4033c463-ad8a-43f4-8ae4-f3949c2cad76.png)

### 1. URI
- 통합 자원 식별자로 자원을 나타내는 유일한 주소를 의미한다.
- URL과 URN 개념을 모두 포함한다.

### 2. URL
- 통합 자원 지시자로 자원의 구체적인 위치를 알려주는 역할을 한다.
- URL은 URI가 될 수 있다.

#### URL 구조

```
<scheme>://<user_name>:<password>@<host>:<port>/<path>?<query>#<fragment>
```

1. **scheme**
    - 사용할 프로토콜
    - 리소스에 어떻게 요청, 접근할 것인지를 명시

2. **사용자 이름과 비밀번호**
    - 어떤 서버들은 자신이 가진 데이터에 접근하기 위해 이름과 비밀번호를 요구한다.
    - ex) [ftp://victolee:12345@호스트/asd.xls](ftp://victolee:12345@xn--9t4b270a0sc/asd.xls)
    - 만약 웹 서버에서 사용자 이름과 비밀번호를 요구하는 URL 스킴을 사용함에도 클라이언트가 이를 명시하지 않고 접근한다면, 기본값으로 '사용자 이름 : anonymous, 비밀번호 : 브라우저에서 제공하는 기본 값'을 따른다.

2. **host와 port**
    - 하나의 host(컴퓨터)여러 개의 프로세스(프로그램)이 각각의 소켓을 사용하여 데이터 통신을 하고 있기 때문에 각각의 소켓을 구분할 필요가 있다.
    - 포트는 소켓을 구분하는 역할
    - HTTP 프로토콜에서 포트 번호를 명시하지 않으면 80번 포트를 기본 값으로 사용한다.
    - ex) [http://www.google.com:80](http://www.google.com/)

3. **path**
    - 호스트에서 제공하는 자원의 경로
    - ex) [https://movie.naver.com/movie/running/current.nhn](https://movie.naver.com/movie/running/current.nhn)

4. **query**
    - Query String(쿼리 스트링)
    - 클라이언트가 자원을 GET 방식으로 요청할 때, 필요한 데이터를 함께 넘겨 줄 목적으로 사용한다.
    - ex) [http://localhost:3000/index?id=3&page=1](http://localhost:3000/index?id=3&page=1)

5. **fragment**
    - HTML에는 각각의 요소에 id 속성을 부여할 수 있다.
    - URL에 프래그먼트를 전달하면 페이지가 해당 id가 있는 곳으로 스크롤이 이동한다.

#### URL 허용 문자

- ASCII 문자만으로 작성하도록 설계되었으나 문제가 있다고 판단하여 ASCII 외의 문자들을 이스케이프 처리하여 ASCII 가 아닌 문자를 안전하게 인코딩한다.
- 비 ASCII는 %로 시작하고 ASCII 코드로 표현되는 이스케이프 문자로 변환한다.

### 3. URN
- 통합 자원 이름으로 자원의 고유한 이름을 나타낸다.

### 4. URL을 입력하면 ??
- 웹 브라우저가 URL을 파싱하고, 문법이 맞으면 퓨니코드로 인코딩한다.
- HSTS(HTTP Strict Transport Security) 목록을 확인해 HTTPS만을 사용해야 한다면 HTTPS로, 아니면 HTTP로 보낸다.
- 그 다음, DNS를 조회하는데 DNS에 요청보내기 전 브라우저에 해당 도메인이 캐싱되어있는지 확인하고 없다면 로컬에 저장된 hosts 파일에서 참조할 수 있는 도메인이 있는지 확인한다.
- 그래도 없다면 DNS로 요청한다. 
- ARP(주소 결정 프로토콜)을 통해 IP와 MAC주소를 알아내고 TCP 통신을 위해 소켓을 연다.
- HTTPS인 경우 TLS handshakd가 추가되고 연결후에 요청을 보내고 응답하여 화면에 표시된다.
