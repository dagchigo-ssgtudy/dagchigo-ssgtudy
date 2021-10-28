# Http Method

## 목차
- Resource 와 method 개념
- 주요 Http Method
- http 속성


## resource 와 method 개념

![무제 7 001](https://user-images.githubusercontent.com/80729831/138912623-41974b64-1f94-4816-910e-7bcdff571c97.jpeg)
![무제 7 002](https://user-images.githubusercontent.com/80729831/138912641-2d27230e-61c9-422f-a495-a03aad8b235b.jpeg)
![무제 7 003](https://user-images.githubusercontent.com/80729831/138912654-d8aafb30-b0c7-4c54-8cf3-101770cf8b11.jpeg)

## 주요 Http Method

![무제 7 004](https://user-images.githubusercontent.com/80729831/138912664-bc03f4b4-ce0a-429a-b6c3-ee20e56aaa53.jpeg)
![무제 7 005](https://user-images.githubusercontent.com/80729831/138912672-267ade7f-74b8-42e3-b5c1-7bf093268165.jpeg)
![무제 7 006](https://user-images.githubusercontent.com/80729831/138912676-45b2836c-0575-455a-bc10-e20a641a9ea0.jpeg)
![무제 7 007](https://user-images.githubusercontent.com/80729831/138912679-8868bdea-599c-417e-9fab-1c1e9e909387.jpeg)
![무제 7 008](https://user-images.githubusercontent.com/80729831/138912684-9dda0525-c3a3-4301-adff-6876912ce5e8.jpeg)
![무제 7 009](https://user-images.githubusercontent.com/80729831/138912687-0a65b0b1-55bb-441a-8359-97077435ba6e.jpeg)

## Http 속성

![무제 7 010](https://user-images.githubusercontent.com/80729831/138912688-46e4d442-382d-4933-9790-8c583055e4ea.jpeg)
![무제 7 011](https://user-images.githubusercontent.com/80729831/138912693-eb7cd4ec-03db-471b-91b8-ed9e7330cb82.jpeg)


## 예상 면접 질문

1. get과 post의 차이점을 말해보세요.

get과 post의 차이점은 2가지가 있습니다.<br />
첫번째 사용 목적은 get은 리소스를 조회할때만 사용합니다. Post는 리소스를 생성할때 사용한다고 했습니다.<br />
두번째는 body유무인데, get은 사용할 수있지만, 지원하지 않는 곳이 많아 사용을 하지않습니다.<br /> 
그래서 길이에 제한이 있고, 쿼리스트링에 정보를 담아 전달하게 되는데 <br />uri에 정보가 다 나타나니 보안에 취약할 수 있기에 중요한 정보는 다루지 않는다고 했습니다. <br />
반대로 post는 바디를 사용하기에 길이에 제한이 없고, 용량이 큰 데이터도 보낼 수 있다고 했습니다. <br />보안도 좋기에 중요한 정보를 보낼때는 웬만하면 포스트를 사용합니다. 
<br /> +추가<br />
마지막은 멱등성인데, 동일한 요청을 여러번 보내는 것과 한 번 보내는 것이 같은지를 나타내는 속성입니다.<br />
get의 경우 동일한 요청에는 동일한 응답만이 오기에 멱등성을 지니고 있어야하지만,<br /> post의 경우 계속해서 새로운 아이디의 데이터를 생성하기에 멱등성을 지니지않고 있습니다.
