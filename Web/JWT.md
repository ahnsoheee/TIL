## JWT (Json Web Token)

- JSON 객체를 통해 안전한 권한을 위해 사용할 토큰을 발급해주는 도구
- 인증, 정보 전달 등에 활용된다.
- Header, Payload, Signature로 구분
    ![image](https://user-images.githubusercontent.com/61968474/134347552-d2f6d771-1327-4faf-9e6d-f09382b67a57.png)

```
eyJpc3MiOiJ2ZWxvcGVydC5jb20iLCJleHAiOiIxNDg1MjcwMDAwMDAwIiwiaHR0cHM6Ly92ZWxvcGVydC5jb20vand0X2NsYWltcy9pc19hZG1pbiI6dHJ1ZSwidXNlcklkIjoiMTEwMjgzNzM3MjcxMDIiLCJ1c2VybmFtZSI6InZlbG9wZXJ0In0
```

### Header 
- 토큰의 유형과 토큰을 검증하는데 필요한 서명 시 사용되는 알고리즘으로 구성된다.
- typ : 토큰의 타입을 지정 -> JWT
- alg : 해싱 알고리즘 -> 보통 HMAC SHA256 / RSA 사용
- JSON 형태의 객체가 base64로 인코딩되는 과정에서 공백, 엔터가 사라진다.
```
{
    "typ": "JWT",
    "alg": "HS256"
}
```


### Payload 
- 토큰에 저장할 데이터들로 구성
- 토큰 생성자의 정보, 생성 일시 등 클라이언트와 서버 간의 주고 받는 값들로 구성된다.
- 정보의 한 '조각'을 클레임이라고 부른다. 
- 클레임은 name과 value의 한 쌍으로 이루어져있다.
- 속성들을 클레임 셋이라고 한다.
- 클레임 종류 : 등록된(registered) 클레임, 공개(public) 클레임, 비공개(private) 클레임

```
{
    "iss": "admin",
    "exp": "1485270000000",
    "name": "developer",
}
```

#### 1. 등록된(registered) 클레임
- 서비스에서 필요한 정보가 아닌, 토큰에 대한 정보를 담기 위해 이름이 이미 정해진 클레임들
- 등록된 클레임의 사용은 모두 선택적이다.
- iss : 토큰 발급자 (issuer)
- sub : 토큰 제목 (subject)
- aud : 토큰 대상자 (audience)
- exp : 토큰의 만료 시간 (expiration), NumericDate 형식
- nbf : Not Before를 의미하며, 토큰 활성 날짜와 비슷한 개념,  이 날짜가 지나기 전까지는 토큰이 처리되지 않는다.
- iat : 토큰 발급 시간 (issued at), 이 값을 사용해 토큰의 age가 얼마나 되었는지 판단할 수 있다.
- jti : JWT의 고유 식별자, 주로 중복 처리를 방지하기 위해 사용한다. 일회용 토큰에 사용하면 유용

#### 2. 공개(public) 클레임
- 충돌이 방지된 이름을 가져야한다.
- 충돌을 방지하기 위해 클레임 이름을 URI 형식으로 짓는다.
    ```
    {
        "https://naver.com/jwt_claims/is_admin": true
    }
    ```

#### 3. 비공개(private) 클레임
- 양측(클라이언트 - 서버) 간 협의하에 사용되는 클레임
- 공개 클레임과 달리 이름이 주옥되어 충돌욀 수 있으므로 유의해야한다.
    ```
    {
        "username": "developer"
    }
    ```

### Signature 
- 헤더와 페이로드를 서명한 값으로 구성된다.
- 헤더의 인코딩값과, 페이로드의 인코딩 값을 합친 후 주어진 비밀키로 해쉬하여 생성한다.
- 서명할 때 헤더에 정의한 알고리즘과 비밀키를 이용해 서명하는데 토큰이 탈취되어 위조나 변조가 되더라도 서명한 값과 비교하기 때문에 데이터가 변조되었는지 확인할 수 있다.
```
    HMAC-SHA256(
        secret,
        base64urlEncoding(header) + '.' +
        base64urlEncoding(payload)
    )
```

### 장점
- 사용자 인증에 필요한 정보를 토큰에 포함하기 때문에 별도의 인증 저장소가 필요없다.
- 많은 프로그래밍 언어에서 지원된다.
- 디버깅과 관리가 용이하다.
- 트래픽에 대한 부담이 낮다.
- REST 서비스로 제공 가능하다.

### 단점
- 토큰은 클라이언트에 저장되어 데이터베이스에서 사용자 정보를 조작하더라도 토큰에 직접 적용할 수 없다.
- claim에 넣는 데이터가 많아질수록 토큰이 길어진다.
- API 호출 시 매 호출마다 토큰 데이터를 서버에 전달해야 하는데 길이가 길면 네트워크 대역폭 낭비가 심할 수 있다.
- Payload에 대한 정보를 암호화하지 않고 단순히 base64로 인코딩만 하기 때문에 중간에 갈취당할 경우 디코딩을 통해 데이터를 볼 수 있다. JWE(JSON Web Encryption)을 통해 암호화하거나 중요한 데이터를 Payload에 넣지 말아야한다.

-[JWT 디버거](https://jwt.io/)
-[참고](https://velopert.com/2389)