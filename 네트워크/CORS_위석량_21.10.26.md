# CORS

## SOP란?
- 기존 웹사이트의 통신 방식 : SOP(Same-Origin Policy, 동일 출처 정책)
- 동일 출처 정책 : 동일한 출처(URL)끼리만 API 등 데이터 접근이 가능하도록 함.  

## 왜 SOP 방식을 썼을까?
- 사용자가 A사이트에 로그인 → 토큰 등의 인증 정보가 브라우저에 저장됨
- 해커가 (링크나 스팸 메일 등을 통해) B(해킹)사이트 접근 유도
- B사이트에 접속하면 해커가 만든 HTML, CSS, JavaScript 코드가 사용자의 브라우저에 받아짐
- 해커의 자바스크립트 코드가 사용자의 브라우저에 저장된 인증 정보를 통해 A사이트에 접근하여 정보를 탈취할 수 있음
- 브라우저는 이를 방지하기 위해 출처가 다른 요청을 못하게 함(SOP)  
  - 웹 기능이 다양해짐 → 다른 출처끼리 자유롭게 데이터를 주고받을 필요가 높아짐

## CORS란?
- Cross-Origin Resource Sharing(교차 출처 자원 공유)의 약자
- 추가 HTTP 헤더를 사용하여, 웹 애플리케이션이 다른 origin의 리소스에 접근할 수 있는 권한을 부여해주는 방식
  - Origin(출처) : 보내고 받는 각각의 위치(웹사이트와 API주소)
  - Resource : 주고 받아지는 데이터
- SOP : 다른 출처간 요청을 막는 것/ CORS : 다른 출처간 요청 제한을 풀어주는 것
<img src="https://user-images.githubusercontent.com/83861190/139061322-3255f0f3-7c81-4b4a-8de2-94dca5b81919.png" width="400" height="300"/>  

## CORS 작동 원리
### 1. 단순 요청(Simple Requests)일 경우
- 단순 요청이란?
  - 1. GET, HEAD, POST 중 하나의 메소드를 사용한 요청
  - 2. 안전한 헤더(Accept, Accept-Language, Content-Language, Content-Type)를 사용한 요청 → 헤더에 특별한 설정을 하지 않고 자동으로 설정한 헤더  
      (Content-Type은 application/x-www-form-urlencoded, multipart/form-data, text/plain 중 하나여야 함)  
      * application/json은 심플 리퀘스트가 아님!
  - 3. 요청의 XMLHttpRequestUpdate 객체에 이벤트 리스너가 없어야 함
  - 4. ReadableStream이 요청에 포함되지 않아야 함  
    → a번~ d번 모두를 충족해야 단순 요청
- 클라이언트와 서버간에 간단한 통신을 하고, CORS 헤더를 사용하여 권한을 처리
<img src="https://user-images.githubusercontent.com/83861190/139062254-16abfc6d-6519-4ad0-addb-eb5e875d0d31.png" width="500" height="300" />

### 2. 인증 정보가 담긴 요청일 경우
- 토큰 등 사용자 식별 정보가 담긴 요청일 때  
  → 브라우저에 저장된 쿠키가 악용될 수 있으므로 더 엄격한 조건이 필요
- 클라이언트 측 : 요청의 옵션에 withCredentials = true로 세팅해야 함
- 서버 측 : 아무 출처나 다 되는 * 등을 사용해선 안 됨
  - 인증 정보를 보낸 쪽의 주소를 정확히 명시해야 하며
  - Access-Control-Allow-Credentials 항목을 true로 설정해야 함
<img src="https://user-images.githubusercontent.com/83861190/139062746-210ca345-59cb-42fb-9b7e-dd2c72059ac8.png" width="500" height="300" />

### 3. 단순 요청이 아닐 경우(Preflight)
- 다른 출처끼리의 요청이 보내질 때 브라우저는 요청에 Origin이라는 header를 추가함(Preflight Request)
- Preflight Request : 요청을 보내는 것도 허락 받아야 함
- Origin에는 요청하는 쪽의 scheme, 도메인, 포트가 담김
- Scheme : 요청할 자원에 접근할 방법, 프로토콜(http 등)
- 요청을 받은 서버는 응답의 헤더에 지정된 Access-Control-Allow-Origin 정보를 실어서 보냄(만약 요청한 쪽의 출처가 등록된 상태면 그 URL도 담겨있음)
- 브라우저는 이 둘을 비교해서 요청할 때 보낸 Origin이 응답에 있으면 안전한 요청으로 간주하여 데이터 전송 허용(Main Request)
<img src="https://user-images.githubusercontent.com/83861190/139062951-1f487746-e451-464d-b627-1b59c340af90.png" width="500" height="600" />
