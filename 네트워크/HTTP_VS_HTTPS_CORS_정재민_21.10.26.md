# HTTP

HTTP는 서버 / 클라이언트 모델을 따라 데이터를 주고받기 위한 가장 기초적인 프로토콜입니다.<br/>
HTTP는 인터넷에서 하이퍼텍스트를 교환하기 위한 통신 규약으로, 80번 포트를 사용하고 있습니다.<br/>
HTTP는 stateless 무 상태성 프로토콜이며, Method Path Version Headers Body 등으로 구성되어 있습니다.<br/>
stateless란 상태가 유지되지 않는 것으로 로그인 상태나 장바구니 등의 정보가 저장되지 않는다는 것입니다.<br/>

## HTTP 구조

![Screenshot from 2021-10-26 01-43-11](https://user-images.githubusercontent.com/81761175/139057759-49385c37-33b0-4fb4-821e-f9b69bbb778f.png)

HTTP의 구조는 요청과 응답이 동일합니다.<br/>
요청의 startLine은 말 그대로 요청의 첫 라인입니다.<br/>
여기서 구성되는 method는 get post put delete option 등등이 있고<br/>
request target은 request가 전송되는 목표 uri<br/>
version은 말 그대로 사용되는 HTTP 버전입니다.<br/>

Headers에는 요청이 전송되는 형식을 보내줍니다.<br/>
target의 host, (예를 들어서 google.com)<br/>
요청 보내는 클라이언트에 대한 정보를 담은 useAgent<br/>
해당 요청이 받을 수 있는 응답 accept<br/>
해당 요청이 끝난 후에 클라이언트와 서버의 연결 유무를 지시하는 connection<br/>
요청을 보내는 body의 타입을 나타내는 content type 등이 있습니다.<br/>

Body는 요청의 실제 메시지/데이터를 담고 있으며 body가 없는 request도 있습니다. (예를 들어서 get 요청)<br/>

응답의 구조는 요청과 거의 같으며 startline에는 상태 코드와 상태 메시지가 있습니다.<br/>

## HTTP 문제점

HTTP의 문제점은 첫 번째로 암호화 기능이 없어 중간자 공격에 취약하다는 점이 있고,<br/>

통신하려는 사이트가 신뢰할 수 있는지 확인이 불가합니다.<br/>
따로 확인 작업이 없기 때문에 다른 사이트가 통신하려는 사이트로 위장이 가능합니다.<br/>
예를 들어서 네이버에 접속했는데 접속한 웹 사이트가 찐 네이버인지 확인이 힘들다는 겁니다.<br/>

마지막으로 통신 내용이 변경 가능하다는 겁니다.<br/>
요청을 보낸 곳과 받은 곳의 출처가 정확히 일치하는지 확인할 길이 없습니다.<br/>

# HTTPS

HTTPS는 앞서 설명드린 http에 데이터 암호화가 추가된 프로토콜입니다.<br/>
HTTP와 다르게 443포트를 사용하며, 네트워크 상에서 중간에 제3자가 정보를 볼 수 없도록 <br/>
ssl 혹은 tls라는 알고리즘을 이용해 내용을 암호화하여 데이터를 전송합니다.<br/>

## HTTPS 특징

![Screenshot from 2021-10-26 01-59-52](https://user-images.githubusercontent.com/81761175/139059661-e34cb4f9-b486-4809-b55c-559b49d0a237.png)

HTTPS의 특징으로는 상호 키가 존재한다는 점입니다.<br/>
서로 다른 a와 b 키를 이용해 데이터를 암호화해서 중간자 공격에 대비하는 것인데요<br/>
최초에는 비대칭키 방식으로 대칭키를 공유하고 이후로는 대칭키로 통신합니다.<br/>
공개 키를 이용해 데이터를 암호화하고 비공개리,(개인키)를 이용해 데이터를 복호화 하는 방식입니다.<br/>
이 방식을 진행하기 앞서 서버와 클라이언트가 서로 확인하는 handShake를 진행합니다.<br/>
클라이언트가 임의의 데이터를 생성해서 서버에 보내면<br/>
서버는 응답으로 임의의 데이터와 CA 인증서를 클라이언트에 보냅니다.<br/>
클라이언트는 인증서가 진짜인지 브라우저에 내장된 CA들의 정보를 통해서 확인을 합니다.<br/>

여기서 CA (certificate authority)는 엄격한 인증 과정을 거친 인증 기관들의 디지털 인증 기관을 말합니다.<br/>
만약 브라우저에 내장된 CA들의 정보와 일치하지 않는다면 브라우저는 안전하지 않을 수 있다는 경고를 보여줍니다.<br/>

이로 인해서 중간자 공격에 대비가 가능하고 신뢰할 수 있는 사이트인지를 확인할 수 있습니다.<br/>

# 차이점

http와 https의 차이점은 보안이라고 할 수 있는데요<br/>
http는 암호화가 추가되지 않았기 때문에 보안에 취약합니다.<br/>
반대로 https는 암호화가 추가되어서 안전하게 데이터를 주고받을 수 있습니다.<br/>

두 번째로 https를 이용하면 암호화 복호화의 과정이 필요하기 때문에 http보다 속도는 느립니다.<br/>
하지만 이는 오늘날에는 거의 체감하지 못할 정도의 차이라고 합니다.<br/>

https는 인증서를 발급하고 유지하기 위한 추가 비용이 발생합니다.<br/>
앞서 말씀드린 CA에서 발급받는 인증서를 이용하기 위해서는 비용을 결제해야 합니다.<br/>

그래서 보안이 필요한 환경에서는 https를 단순 정보 조회만을 처리한다면 http를 사용하는 게 적절하다고 합니다.<br/>

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

요청 방식은 3가지가 있는데 첫 번째로 단순 요청 simple Request입니다.
CORS 정책에서 브라우저는 기본적으로 preflight 방식으로 요청하도록 합니다.
하지만 일부 요청은 preflight 방식으로 요청하지 않습니다.
브라우저는 요청을 분석하여 해당 조건을 충족할 때 Simple Request 방식으로 요청합니다.

첫 번째로 HTTP Method가 GET, POST , HEAD 이 셋 중에 하나로 요청한 경우
(HEAD 메서드는 GET 메서드의 요청과 동일한 응답을 요구하지만, 응답 본문을 포함하지 않습니다.)

두 번째로 Fetch 표준 정책에서 정의한 Forbidden Header Name이라는 헤더 목록과
CORS-safelisted request header라는 헤더 목록 이외에 다른 커스텀 헤더
그리고 권한과 관련된 헤더가 없는 경우를 말하는데
한마디로 커스텀 헤더를 전송하지 않는 경우입니다.

세 번째로 HTTP Method가 POST인 경우에는
Content-Type 헤더를 수동으로 지정할 수 있는데,
이 Content-Type이 다음과 같은 세 가지 값에 포함되는 경우입니다.
application/x-www-form-urlencoded, multipart/form-data, text/plain 입니다.

Simple Request는 서버에 1번 요청하고, 서버도 1번 회신하는 것으로 처리가 종료됩니다.

## Preflighted Requests

![preflight_correct (1)](https://user-images.githubusercontent.com/81761175/139064965-f4ca6dbe-ee8d-4f87-8a8e-0427a3225044.png)

Preflight Request는 비행하기 전이라는 뜻으로 쉽게 말하면 이륙 허가를 받는 것입니다.
가장 먼저 HTTP Request Method 중 하나인 OPTION 메서드를 교차 출처로 보내고,
응답받은 헤더 정보를 통해서 메인 요청을 보낼 수 있는지 판단하는 방식입니다.
브라우저는 요청에 origin이라는 header를 추가합니다.
origin에는 요청하는 쪽의 scheme, 도메인, 포트가 담깁니다.
(scheme은 요청할 자원에 접근할 방법)
브라우저는 이 둘을 비교해서 요청할 때 보낸 origin이 응답에 있으면 이를 허용해 줍니다.

## Requests with credentials

![cred-req-updated](https://user-images.githubusercontent.com/81761175/139065076-60ba0fe8-e4f3-4cac-9460-cfaaed231951.png)

Request with credential은 인증 정보를 포함하여 요청하는 방식입니다.
CORS 요청은 기본적으로 Non-Credential 요청이므로, withCredentials = true를
지정하지 않으면 Non-Credential 요청이 됩니다.
그래서 요청 시 withCredentials = true를 지정해서 Credential 요청을 보낼 수 있고,
서버는 Response Header에 반드시 Access-Control-Allow-Credentials: true를 포함해야 합니다.
Access-Control-Allow-Origin 헤더의 값에는 *가 오면 안 되고 http://foo.origin과 같은 구체적인 도메인이 와야 합니다.
