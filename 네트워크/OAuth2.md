<image src='https://images.velog.io/images/yoon63/post/ffa2fb95-4705-40d7-ac9a-5b1340809f8e/image.png' width='20%' height='20%'/>

## OAuth란?

> Open Authentication의 줄임말
> 
> 유저가 다른 웹사이트 상의 자신들의 정보에 대해
웹사이트나 애플리케이션의 *접근 권한을 부여*할 수 있는 공통적인 수단으로서 사용되는,   
접근 위임을 위한 개방형 표준이다.

### OAuth 2.0의 구성 요소
- **Client** : 	OAuth 2.0을 사용해 서드파티 로그인 기능을 구현할 애플리케이션
- **Resource Owner** : 서드파티 애플리케이션에 있는 개인정보(리소스)를 이용해 Client가 제공하는 서비스를 이용하려는 사용자
- **Resource Server** : 사용자의 개인정보를 가지고있는 애플리케이션 서버. Client는 Token을 이 서버로 넘겨 개인정보를 응답 받을 수 있다.
- **Authorization Server** : 권한을 부여해주는 서버. 사용자는 이 서버에서 Authorization Code를 발급 받을 수 있다.
Client는 이 서버로 Authorization Code을 넘겨 Token을 받급 받을 수 있다.

### OAuth 2.0 동작과정
> < 가장 기본이 되는 방식 >
>
> 사용자가 인증 요청을 하면, Client기 Authorization Server에 인가 요청을 하고
Authorization Server로부터 Authorization Code를 발급받는다.
다시 Authroization Server에 Authorization Code를 제시하여 Token을 요청하고, 발급된 Token을 통해 Resource Server에 사용자의 데이터를 요청한다.


권한 부여 방식에 따라 4가지 프로토콜로 나뉜다.

**1. Authorization Code Grant** : 권한 부여 승인 코드 방식   
권한 부여 승인을 위해 자체 생성한 *Authorization Code*를 전달하는 방식으로 많이 쓰이고 *기본*이 되는 방식. Refresh Token 사용 가능   
=> 권한 부여 승인 요청 시 response_type을 code로 지정하여 요청   
<image src='https://images.velog.io/images/yoon63/post/5bc91813-f7d2-43bf-90ea-dadb08b82e55/image.png' width='50%' height='50%' />   

**2. Implicit Grant** : 암묵적 승인 방식   
자격증명을 안전하게 저장하기 힘든 클라이언트(JS등 스크립트 언어를 사용한 브라우저)에게 최적화된 방식.
권한 부여 승인 코드 없이 바로 Access Token이 발급. Refresh Token 사용이 불가능한 방식이며, 이 방식에서 권한 서버는 client_secret를 사용해 클라이언트를 인증하지 않음.   
=> 권한 부여 승인 요청 시 response_type을 token으로 설정   
<image src='https://images.velog.io/images/yoon63/post/5c2773dd-ad90-49ae-a553-bd91ee7002b5/image.png' width='50%' height='50%' />   


**3. Resource Owner Password Credentials Grant** : 자원 소유자 자격증명 승인 방식   

간단하게 username, password로 Access Token을 받는 방식.   
자신의 서비스에서 제공하는 어플리케이션일 경우에만 사용되는 인증 방식. Refresh Token의 사용도 가능.   
=> 권한 서버, 리소스 서버, 클라이언트가 모두 같은 시스템에 속해 있을 때만 가능   

<image src='https://images.velog.io/images/yoon63/post/54b6b57c-d150-418f-a4a6-0cc4a8035f43/image.png' width='50%' height='50%' />   


**4. Client Credentials Grant** : 클라이언트 자격증명 승인 방식   
클라이언트 자신이 관리하는 리소스 혹은 권한 서버에 해당 클라이언트를 위한 제한된 리소스 접근 권한이 설정되어 있는 경우 사용.   
이 방식은 자격증명을 안전하게 보관할 수 있는 클라이언트에서만 사용되어야 하며, Refresh Token은 사용 불가.   

<image src='https://images.velog.io/images/yoon63/post/0a8c5a7e-f32f-49a1-ac33-5a328b63d5ad/image.png' width='50%' height='50%' />   

### OAuth 2.0의 취약점
1. CSRF 공격을 통한 계정 탈취
	- CSRF 공격으로 피해자 계정에 공격자의 계정을 연동
    - authorization code를 주고받을때 state 파라미터를 넣어 서로간에 검증을 하는데, 이 state값에 대한 검증이 누락되어있거나 미흡할경우 사용자 계정을 탈취 할 수있다. 
    => state값에 대한 정책과 사용여부, 방법에 대해 공격 가능 여부를 확인 필요
2. Covert Redirect
	- OAuth 2.0 인증 과정에서 `redirect_uri` 파라미터 값에 대한 검증이 누락되거나 미흡할 때 발생하는 취약점
    - 피해자에게 변조된 Redirect Uri를 보내 로그인을 유도 -> Authorization code가 공격자에게 전달 -> 계정 탈취
    <image src='https://images.velog.io/images/yoon63/post/6d787574-0a81-4fb2-a9aa-52b42e3abafb/image.png' width='50%' height='50%' />   
    
    => Full Path 검증 필요
    
  <details>
   <summary>+) 보안 검수 항목</summary>
                                                                                                                           
  ![](https://images.velog.io/images/yoon63/post/350203c4-5b0d-4572-8ed2-08352d3a840a/image.png)
  </details>
  
  ---
 ### OAuth 1.0 -> OAuth 2.0?
<image src='https://images.velog.io/images/yoon63/post/681601db-bbff-404f-a088-a0a8916b67d1/image.png' width='50%' height='50%' />   

- OAuth 1.0의 한계
  - 웹 어플리케이션만 가능
  - 절차가 복잡하여 OAuth 구현 라이브러리를 만드는 것도 어렵고 OAuth 인증을 제공해주는 서비스 측에서도 연산에 부담이 발생하는 단점
- OAuth 2.0의 특징
  - 별도 암호화가 필요없이 HTTPS를 사용
  - Access Token에 Life-Time을 지정할 수 있도록 함. (OAuth 1.0에서는 지원X)
