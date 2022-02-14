## OAuth (Open Authorization)

- 하나의 인증 서비스로 여러 서비스의 인증 및 권한 부여를 위한 표준 프로토콜
- 하나의 플랫폼의 권한으로 다양한 플랫폼에서 권한을 행사할 수 있다.
- 로컬 로그인을 사용하면 사용자의 개인 정보를 직접 관리해야 하는데 OAuth를 사용하면 서드파티 앱에게 위임할 수 있다.

### 참여자
1. Resource Server: 사용자의 개인 정보를 가진 어플리케이션 서버
    - 네이버, 구글
2. Authoriztion Server: 인증을 담당하는 서버
    - 인증 서버: 깃허브 인증 서버, 네이버, 구글
3. Client: Resource Server에 접속해 정보를 가져오고자 하는 웹 어플리케이션
    - OAuth를 사용하는 어플리케이션
4. Resource Owner: 자원의 소유자
    - 일반 사용자
- 1, 2가 하나의 서버처럼 동작하는 경우도 있다.

### OAuth 2.0 프로세스

<img width="798" alt="스크린샷 2022-02-14 오후 10 12 58" src="https://user-images.githubusercontent.com/61968474/153870757-82096eac-568b-4a48-942c-94bf171ae355.png">

### Client 등록
- Client ID: 사용되는 Application 아이디
- Client Secret: 외부에 절대로 노출되어서는 안되는 코드
- Redirect URL: Authorization code를 전달받을 주소
- GitHub, Google 등 외부 서비스를 통해 인증을 마치면 Authorization code를 발급하고 명시된 주소로 리다이렉트 시킨다.
- 클라이언트는 Authorization code와 Client ID, Client Secret을 Resource Server에 보내 자원을 사용할 수 있는 액세스 토큰을 발급받는다.
- 등록되지 않는 redirect URL을 사용하는 경우 Resource Server가 인증을 거부한다.

### Resource Owner의 승인
- 로그인 버튼을 클릭했을 때 링크로 제공하기만 하면 된다.
```
https://resource_server/?client_id=1&scope=B,C&redirect_uri=https://client/callback
```
- 로그인이 성공하면 Client ID가 같은지 확인한다.
- Client ID가 가진 Redirect URL과 비교 후 같으면 Resource Owner에게 scope에 해당하는 기능을 할 수 있도록 Client에게 부여할 것인지 물어보는 메세지를 보낸다.
- 허용하면 Resource Server는 user id와 scope를 저장한다. (scope: 권한의 범위)

### Resource Server의 승인
- Resource Server는 Authorization code를 Owner에게 전송한다.
```
Location : https://client/callback?code=3
```
- Owner는 은밀하게 Client로 이동해서 Client가 Authorization code를 갖게 된다.
- Client는 Authorization code와 Client ID, Secret 값을 Resource Server에게 전송하고 액세스 토큰을 요청한다.
- Resource Server는 Authorization code를 확인하고 Client ID, secret, URL을 확인 후에 액세스 토큰을 발급한다.

### 액세스 토큰 발급
- 다시 인증을 안하기 위해 Resource Server와 Client의 Authorization code를 삭제한다.
- Resource Server는 Client에게 액세스 토큰을 전송하고, Client는 발급받은 토큰을 저장한다.


<details>
<summary>참고</summary>

- https://d2.naver.com/helloworld/24942
- https://developers.payco.com/guide
- https://datatracker.ietf.org/doc/html/rfc6749
- [생활코딩-OAuth](https://opentutorials.org/course/3405/22004)
</details>