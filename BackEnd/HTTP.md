## **HTTP**
    
> - HTTP(Hyper Text Transfer Protocal) 서버/클라이언트 모델을 따라 데이터(이미지, HTML, 텍스트파일, 동영상, 음성 파일)를 주고 받기 위한 프로토콜입니다.  
> - HTTP는 애플리케이션 레벨의 프로토콜로 TCP/IP 위에서 작동합니다. 
> - HTTP는 상태를 가지고 있지 않는 Stateless 단방향 프로토콜이며 Method, Path, Version, Headers, Body 등으로 구성됩니다.


<details>
<summary>메시지</summary>
<div markdown="1">
  
- 요청
    
    ![Untitled](https://mdn.mozillademos.org/files/13687/HTTP_Request.png)
    
    - Method :  보통 클라이언트가 수행하고자 하는 동작을 정의한 GET,POST,OPTIONS,HEAD등등
    - Path:   [프로토콜](https://developer.mozilla.org/ko/docs/Glossary/Protocol) (`http://`), [도메인](https://developer.mozilla.org/en-US/docs/Glossary/Domain) 리소스의 URL입니다.
    - HTTP 프로토콜의 버전.
    - 서버에 대한 추가 정보를 전달하는 선택적 [헤더들](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers).
- 응답
    
    ![Untitled](https://mdn.mozillademos.org/files/13691/HTTP_Response.png)
    
    - HTTP 프로토콜의 버전.
    - 요청의 성공 여부와, 그 이유를 나타내는 [상태 코드](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).
    - 아무런 영향력이 없는, 상태 코드의 짧은 설명을 나타내는 상태 메시지.
    - 요청 헤더와 비슷한, HTTP [헤더들](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers).
    - 선택 사항으로, 가져온 리소스가 포함되는 본문.

</div>
</details>

<details>
  <summary>메서드</summary>
  <div markdown="1">
    
- HTTP 명세는 공통 요청 메서드의 집합을 정의하고 있음
    
- 요청 메시지에 따라 본문이 있을 수도 있고 없을 수도 있음
    
- 확장 메서드: HTTP 명세를 확장하여 추가로 구현된 메서드

    ![image](https://user-images.githubusercontent.com/53087860/139631952-291625a9-fcf7-4c7b-9919-83d819d4c12c.png)
- 안전한 메서드 (Safe Method)
    - HTTP는 안전한 메서드라고 불리는 메서드의 집합을 정의
    - `GET`, `HEAD`는 안전하다고 정의할 수 있는데, HTTP 요청의 결과로 서버에 어떤 작용도 없기 때문
    - 안전한 메서드의 목적은, 서버에 영향을 줄 수 있는 안전하지 않은 메서드가 사용될 때 사용자에게 알려줄 수 있는 HTTP 애플리케이션을 만들도록 하는 것에 있음
- GET
    - 가장 흔하게 쓰이는 메서드
    - 주로 서버에게 리소스를 달라고 요청하기 위해 쓰임
- HEAD
    - 정확히 `GET`처럼 행동하지만, 서버는 응답으로 헤더만을 돌려줌. 엔터티 본문은 반환되지 않음
        - 리소스를 가져오지 않고도 타입 등을 알아낼 수 있음
        - 응답의 상태 코드를 통해 개체가 존재하는지 확인 가능
        - 헤더를 확인하여 리소스가 변경됐는지 검사할 수 있음
    - HTTP/1.1 준수를 위해서는 `HEAD` 메서드가 반드시 구현되어 있어야 함
- PUT
    - 서버가 요청의 본문을 가지고 요청 URL의 이름대로 새 문서를 만들거나, 이미 URL이 존재한다면 본문을 사용해서 교체
    - 콘텐츠를 변경할 수 있게 해줌; 사용자에게 로그인 요구
- PATCH
    - **HTTP PATCH** 메소드는 리소스의 부분적인 수정을 할 때에 사용됩니다.
- POST
    - 서버에 입력 데이터를 전송하기 위해 설계
    - HTML 폼을 지원하기 위해 흔히 사용되며, 채워진 폼에 담긴 데이터는 서버로 전송되고 서버는 이를 모아 필요로 하는 곳에 보냄
- TRACE
    - 클라이언트에게 자신의 요청이 서버에 도달했을 때 어떻게 보이게 되는지 알려줌
    - 목적지 서버에서 ‘루프백(loopback)’ 진단을 함; 서버는 요청 메시지를 본문에 넣어 `TRACE` 응답을 되돌려줌
    - 주로 진단할 때나 프락시/타 애플리케이션 요청에 어떤 영향을 미치는지 확인하고자 할 때 사용
    - 서버의 엔터티 본문을 리턴받지 않고 서버가 받은 요청이 그대로 엔터티 본문에 들어 있음
- OPTIONS
    - 서버에게 여러 가지 종류의 지원 범위에 대해 물어봄; 특정 리소스에 어떤 메서드가 지원되는지
- DELETE
    - 서버에게 요청 URL로 지정한 리소스를 삭제할 것을 요청
    - 단, 삭제 수행 보장은 못함; 서버가 클라이언트에게 알리지 않고 요청 무시하는 것을 허용하기 때문
- 확장 메서드
    - HTTP/1.1 명세에 정의되지 않은 메서드로, 필요에 따라 확장해도 문제가 없도록 설계되어 있기 때문에 과거 구현한 소프트웨어의 오동작을 유발하지는 않음
    - ‘Be conservative in what you send, be liberal in what you accept.’ (엄격하게 보내고 관대하게 받아들여라)
        - 프락시는 종단 간(end-to-end) 행위를 망가뜨리지 않을 수 있다면 알려지지 않은 메서드가 담긴 메시지를 다운스트림 서버로 전달하려고 시도, 그렇지 않다면 `501 Not Implemented` 상태 코드로 응답해야 함
    
  </div>
  </details>
    
<h4> 데이터 구분</h4>

  - HTTP는 수천 개의 데이터 타입을 다루기 때문에 ‘**MIME (Multipurpose Internet Mail Extensions, 다목적 인터넷 메일 확장)**‘라는 데이터 포맷 라벨을 웹에서 전송되는 객체 각각에 붙임
  - 쉽게 말하면, 이 웹 콘텐츠가 어떤 데이터 타입인지 알려주는 라벨
  - 표현 형식: ‘주 타입/부 타입’
      - HTML 데이터 타입 = ‘text/html’
      - JPEG 이미지 데이터 타입 = ‘image/jpeg’
      - GIF 이미지 데이터 타입 = ‘image/gif’
   

#### 웹 클라이언트와 서버 기초 동작방식

  ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e597085f-ba38-4ec0-adaf-4307b42e4fca/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20211101%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211101T070115Z&X-Amz-Expires=86400&X-Amz-Signature=becd6a9496c702242e7eb2f1bab9618013105d313cfc8e14c3c92fb3a2db0e13&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
  - 웹 서버: 인터넷의 데이터 저장 및 HTTP 클라이언트가 요청한 데이터 제공
  - 웹 클라이언트: 웹 서버에 HTTP 요청

## HTTP 예상 질문
1. HTTP reqeust에는 어떤 것들이 있나요
> GET : 존재하는 자원에 대한 요청
> 
> POST : 새로운 자원을 생성
> 
> PUT : 존재하는 자원에 대한 변경
> 
> DELETE : 존재하는 자원에 대한 삭제
> 
> HEAD : 서버 헤더 정보를 획득. GET과 비슷하나 Response Body를 반환하지 않음
> 
> OPTIONS : 서버 옵션들을 확인하기 위한 요청. CORS에서 사용
> 
2. 브라우저에 URL을 입력하고 요청한 페이지를 볼때까지 어떤 일이 일어나는가?
> 1. 웹 브라우저는 서버의 URL에서 호스트 명을 추출
> 
> 2. 웹 브라우저는 서버의 호스트 명을 IP로 변환
> 
> 3. 웹 브라우저는 URL에서 포트번호 있으면 추출
> 
> 4. 웹 브라우저는 웹 서버와 TCP 커넥션을 맺음
> 
> 5. 웹 브라우저는 서버에 HTTP 요청을 보냄
> 
> 6. 서버는 브라우저에게 HTTP 응답을 돌려줌
> 
> 7. 커넥션이 닫히면 웹 브라우저는 문서를 보여줌
> 
3. HTTP 요청과 응답 헤더에 어떤 내용이 들어가는가?
> 헤더 종류
>    - 일반 헤더
>        
>        클라이언트와 서버 양쪽 모두가 사용. 이들은 클라이언트, 서버 그리고 어딘가에 메시지를 보내는 다른 애플리케이션들을 위해 다양한 목적으로 사용
>        
>        - 일반 캐시 헤더 : 매번 원 서버로부터 객체를 가져오는 대신 로컬 복사본으로 캐시할 수있도록 해주는 헤더
>    - 요청 헤더
>        
>        요청 메시지를 위한 헤더, 서버에게 클라이언트가 받고자 하는 데이터의 타입와 같은 부가 정보를 제공
>        
>        - Accept 관련 헤더 : 클라이언트가 무엇을원하고 무엇을 할 수 있는지, 무엇을 원치 않는 지
>        - 조건부 요청헤더 : 서버에게 요청에 응답하기전에 먼저 조건이 참인지확인하게 하는 제약을 포함
>        - 요청 보안 헤더 : HTTP 자체적으로 요청을 위한 간단한 인증 체계
>        - 프락시 요청 헤더 : 그들의 기능을 돕기 위해 기능
>    - 응답 헤더
>        
>        서버가 클라이언트에게 정보를 제공하기 위한 자신만의 헤더를 갖고 있음
>        
>        협상 헤더 : 서버와 클라이언트가 어떤 표현을 택할 것인지 협상
>        
>        보안 헤더 : 요청에 대한 보안 헤더
>       
>    - Entity 헤더
>        
>        엔티티 본문에 들어있는 데이터의 타입이 무엇인지 알려줌
>        예) Content-Type : text/html; charset=iso-latin-1
>        
>        콘텐츠 헤더 : 엔티티의 콘텐츠에 대한 구체적인 정보를 제공
>        
>        엔터티 캐싱 헤더 : 엔티티 캐싱에 대한 정보를 제공함 예) 리로스에 대해 캐시된 사본이 아직 유효한지에 대한 정보와, 캐시된 리소스가 더 이상 유효아지 않게 되는 시점을 더 잘 추정하기 위한 단서
>        
>    - 확장 헤더
>        
>        애플리케이션 개발자들에 의해 만들어졌지만 아직 승인된 HTTP 명세에는 추가되지 않은 비표준 헤더





## 그 외의 관련 개념
<details>
<summary>트랜잭션</summary>
<div markdown="1">

> HTTP 트랜잭션은 요청명령과 응답 결과로 구성
</div>
</details>
    
<details>
<summary>리소스</summary>
<div markdown="1">

> 웹 리소스는 웹 콘텐츠의 원천
</div>
</details>

  
  
  
