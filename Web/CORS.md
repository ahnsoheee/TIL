## CORS (Cross Origin Resource Sharing)

- 추가적인 HTTP 헤더를 이용해 다른 어플리케이션이 리소스에 접근할 수 있도록 하는 것이다.
- 다른 origin에서 내 리소스에 접근하지 못하게 하기 위해서도 사용한다.

    origin : URL에서 protocol, host, port를 합친 것
- 도메인이 서로 다른 사이트 간의 API를 요청할 때 공유를 설정하지 않으면 CORS 에러가 발생한다.
- 요청하는 쪽의 헤더와 요청받는 쪽의 헤더의 값을 설정해야 한다.
- CORS는 브라우저가 사용하는 것이기 때문에 서버에서 서버로 보내는 요청은 CORS가 적용되지 않는다.

    => 프록시 서버를 추가로 만들어서 클라이언트에서 프록시 서버로 요청을 보내고 프록시 서버에서 요청을 보내면 브라우저가 개입되지 않았기 때문에 CORS 오류를 피할 수 있다.

### CORS의 동작 과정

#### Simple request

![image](https://user-images.githubusercontent.com/61968474/132084299-82c5a558-9a3a-4db5-a3f2-d21e3e36ae8d.png)

- 서버에게 바로 요청을 보내는 방법
- CORS Preflight Request(사전 요청)을 발생시키지 않는 요청
- 서버에 API를 요청하고 서버는 Access-Control-Allow-Origin 헤더를 포함한 응답을 브라우저에 보낸다. 
- 브라우저는 Access-Control-Allow-Origin 헤더를 확인해서 CORS 동작을 수행할지 판단한다.

**Simple request 조건**
- 요청 메소드가 GET, HEAD, POST 중 하나여야 한다.
- Accept, Accept-Language, Content-Language, Content-Type, DPR, Downlink, Save-Data, Viewport-Width, Width를 제외한 헤더를 사용하면 안 된다.
- Content-Type 헤더는 application/x-www-form-urlencoded, multipart/form-data, text/plain 중 하나를 사용해야 합니다.

=> 인증 시 사용되는 Authorization 헤더가 포함되지 않으며, 많은 API들이 Content-Type으로 application/json을 사용하기 때문에 어려운 조건이다.

#### Preflight request
- 서버에 예비 요청을 보내 안전한지 판단한 후 본 요청을 보내는 방법

![image](https://user-images.githubusercontent.com/61968474/132084432-e17a3c0d-9ae8-4979-89ab-a43fe0fbee01.png)

- OPTIONS 메소드를 통해 예비 요청을 보내 실제 요청을 전송할지 판단한다.
- 서버는 요청에 대한 응답으로 Access-Control-Allow-Origin 헤더를 포함한 응답을 브라우저에 보낸다.
- 브라우저는 Access-Control-Allow-Origin 헤더를 확인해서 CORS 동작을 수행할지 판단한다.

#

=>  브라우저가 리소스를 요청할 때 추가적인 헤더에 정보를 담는다.

-> 요청 헤더에 origin은 무엇이고 어떤 메소드를 사용해 요청할 것인지 어떤 헤더를 포함할 것인지를 담아 서버에 전송한다.

-> 서버는 서버가 응답할 수 있는 origin들을 담아 브라우저에게 보낸다.

-> 브라우저가 이 헤더를 보고 해당 origin에서 요청할 수 있다면 리소스 전송을 허용하고 만약 불가능하다면 에러를 발생시킨다.
