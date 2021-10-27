# SOP

![52930297-3853d680-338b-11e9-91c8-d240d36cb87e](https://user-images.githubusercontent.com/81761175/139060222-84d1889d-f466-4126-8569-db3053384a6b.png)

다음은 CORS에 대해서 설명드리겠습니다.<br/>
여러분들은 프로젝트를 진행하면서 이 에러를 본 적이 분명 있을 겁니다.<br/>

이 에러는 CORS 정책에 의해서 발생한 에러인데,<br/>
이의 근원은 same origin policy, SOP입니다.<br/>
SOP는 어떤 출처에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 보안 정책입니다.<br/>

이를 기반으로 CORS 정책이 생겨난 유래를 살펴봅시다.<br/>

# CORS

![Screenshot from 2021-10-26 03-27-08](https://user-images.githubusercontent.com/81761175/139061349-498b17d2-72cc-4399-a203-4379dc4d220f.png)

예전에 웹은 하나의 서버에서 비즈니스 로직과 HTML 페이지 빌드를 같이 하는 게 일반적이었습니다.<br/>
한마디로 같은 서버에서 모든 것이 이뤄졌다는 거죠<br/>

당시에는 다른 서버로 요청을 날린다고 하면 이는 분명<br/> 
뭔가 개인 정보 유출, 피싱 사이트와 같이 악의적인 행동일 것이라고 의심을 했습니다.<br/>
그랬기 때문에 웹 브라우저에서는 같은 출처가 아니면 이를 SOP 보안정책으로서 요청 자체를 막는 선택을 하였습니다.<br/>

하지만 점점 웹사이트에서 할 수 있는 일이 많아지면서 기존 웹 브라우저 보안 정책 때문에 불편한 점들이 생기기 시작했습니다.<br/>
예를 들어서 날씨 api를 받아오거나 지도 api를 받아야 하는지 등이 있습니다.<br/>
하지만 SOP 정책에 요청이 막히자 많은 개발자들은 이 정책을 JSONP 라는 방식으로 우회하여 이를 피했습니다.<br/>
이러한 현상 때문에 웹브라우저는 특정 조건에 맞는 경우라면 다른 출처라도 리소스 공유가 가능하도록 해주었고, <br/>
이게 바로 Cross-Origin Resource Sharing, CORS 정책입니다.

CORS는 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는<br/>
권한을 부여하도록 브라우저에 알려주는 체제입니다.<br/>

여기서 많이들 착각하는 게 앞서 보여드렸던 에러는 CORS 로 인해서 에러가 발생하는 게 아니고<br/>
SOP 로 인해 에러가 발생하는 겁니다.<br/>
CORS 는 이를 허용해 주기 위한 정책입니다.<br/>

서버에서는 특정 METHOD나 특정 도메인에만 권한을 부여하도록 설정 가능하고,<br/>
데이터 통신 시간은 최대 몇 초까지 가능하다는 규칙들이 있습니다.<br/>

만약 웹 애플리케이션을 A라고 하고 다른 출처를 B라고 하면,<br/>
A가 B가 가진 자원을 사용하겠다고 요청을 하고,<br/>
B는 본인이 정해놓은 허용 기준에 A가 맞는다면 이를 사용할 수 있도록 권한을 주어 허용해 주며,<br/>
이를 사용하기 위한 약간의 규칙을 알려준다는 과정이라고 보면 쉽습니다.<br/>

# CORS Request

## Simple Request

![Screenshot from 2021-10-26 03-49-46](https://user-images.githubusercontent.com/81761175/139064565-0db01c32-86b2-435a-b86b-90a3ded10eba.png)

요청 방식은 3가지가 있는데 첫 번째로 단순 요청 simple Request입니다.<br/>
CORS 정책에서 브라우저는 기본적으로 preflight 방식으로 요청하도록 합니다.<br/>
하지만 일부 요청은 preflight 방식으로 요청하지 않습니다.<br/>
브라우저는 요청을 분석하여 해당 조건을 충족할 때 Simple Request 방식으로 요청합니다.<br/>

첫 번째로 HTTP Method가 GET, POST , HEAD 이 셋 중에 하나로 요청한 경우<br/>
(HEAD 메서드는 GET 메서드의 요청과 동일한 응답을 요구하지만, 응답 본문을 포함하지 않습니다.)<br/>

두 번째로 Fetch 표준 정책에서 정의한 Forbidden Header Name이라는 헤더 목록과<br/>
CORS-safelisted request header라는 헤더 목록 이외에 다른 커스텀 헤더<br/>
그리고 권한과 관련된 헤더가 없는 경우를 말하는데<br/>
한마디로 커스텀 헤더를 전송하지 않는 경우입니다.<br/>

세 번째로 HTTP Method가 POST인 경우에는<br/>
Content-Type 헤더를 수동으로 지정할 수 있는데,<br/>
이 Content-Type이 다음과 같은 세 가지 값에 포함되는 경우입니다.<br/>
application/x-www-form-urlencoded, multipart/form-data, text/plain 입니다.<br/>

Simple Request는 서버에 1번 요청하고, 서버도 1번 회신하는 것으로 처리가 종료됩니다.<br/>

## Preflighted Requests

![preflight_correct (1)](https://user-images.githubusercontent.com/81761175/139064965-f4ca6dbe-ee8d-4f87-8a8e-0427a3225044.png)

Preflight Request는 비행하기 전이라는 뜻으로 쉽게 말하면 이륙 허가를 받는 것입니다.<br/>
가장 먼저 HTTP Request Method 중 하나인 OPTION 메서드를 교차 출처로 보내고,<br/>
응답받은 헤더 정보를 통해서 메인 요청을 보낼 수 있는지 판단하는 방식입니다.<br/>
브라우저는 요청에 origin이라는 header를 추가합니다.<br/>
origin에는 요청하는 쪽의 scheme, 도메인, 포트가 담깁니다.<br/>
(scheme은 요청할 자원에 접근할 방법)<br/>
브라우저는 이 둘을 비교해서 요청할 때 보낸 origin이 응답에 있으면 이를 허용해 줍니다.<br/>

## Requests with credentials

![cred-req-updated](https://user-images.githubusercontent.com/81761175/139065076-60ba0fe8-e4f3-4cac-9460-cfaaed231951.png)

Request with credential은 인증 정보를 포함하여 요청하는 방식입니다.<br/>
CORS 요청은 기본적으로 Non-Credential 요청이므로, withCredentials = true를<br/>
지정하지 않으면 Non-Credential 요청이 됩니다.<br/>
그래서 요청 시 withCredentials = true를 지정해서 Credential 요청을 보낼 수 있고,<br/>
서버는 Response Header에 반드시 Access-Control-Allow-Credentials: true를 포함해야 합니다.<br/>
Access-Control-Allow-Origin 헤더의 값에는 *가 오면 안 되고 http://foo.origin과 같은 구체적인 도메인이 와야 합니다.<br/>
