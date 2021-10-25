# Node.js
<img src="https://user-images.githubusercontent.com/83910753/138738753-c89db2e1-1001-4232-9d0e-7c9dc09d75b9.png" width="20%" height="20%">

- [Node.js란?](https://github.com/seyoonkim48/im-sprint-practice-deploy/wiki/_new#nodejs%EB%9E%80)
- [Node.js 코어 컨셉](https://github.com/seyoonkim48/im-sprint-practice-deploy/wiki/_new#nodejs-%EC%BD%94%EC%96%B4-%EC%BB%A8%EC%85%89)
- [Node.js 예상 질문](https://github.com/seyoonkim48/im-sprint-practice-deploy/wiki/_new#nodejs-%EC%98%88%EC%83%81-%EC%A7%88%EB%AC%B8)
- [그 외 관련 개념](https://github.com/seyoonkim48/im-sprint-practice-deploy/wiki/_new#%EA%B7%B8-%EC%99%B8%EC%9D%98-%EA%B4%80%EB%A0%A8-%EA%B0%9C%EB%85%90)
- [참고 사이트](https://github.com/seyoonkim48/im-sprint-practice-deploy/wiki/_new#%EC%B0%B8%EA%B3%A0-%EC%82%AC%EC%9D%B4%ED%8A%B8)

<br>

## Node.js란?
> - Chrome V8 JavaScript 엔진으로 빌드된 JavaScript 런타임, 이벤트 기반의 플랫폼
> - 브라우저에서만 작동하던 JavaScript를 확장성 있는 네트워크 애플리케이션 개발에 사용할 수 있도록 설계된 JavaScript 런타임

<br>

## Node.js 코어 컨셉

**비동기 처리**
> JS의 비동기란 ‘특정 코드의 실행이 완료될 때까지 기다리지 않고 *다음 코드를 먼저 수행*하는 자바스크립트의 특성’을 의미   
> Node.js에서 비동기 처리는 이벤트 방식으로 이루어지며, 이벤트(요청)가 발생하면 해당 작업은 백그라운드로 보내고 다른 작업을 시작한다.

**Non-Blocking I/O**
> Blocking I/O : 자신의 작업을 진행하다가 다른 주체의 작업이 시작되면 다른 작업이 끝날때까지 기다렸다가 자신의 작업을 시작하는 것   
> Non-Blocking I/O : 다른 주체의 작업의 시작에 상관없이 자신의 작업을 하는 것   
>   
> Node.js는 비동기적 논블로킹 I/O 방식으로, 다른 주체가 작업을 마치면 콜백의 호출로 완료를 알게된다.   
> <img src="https://user-images.githubusercontent.com/83910753/138731913-4f2eec4d-8f6e-41d4-bf61-513feb2cde53.png" width="300" height="300">   

**싱글 스레드**
> Node.js는 싱글스레드, 논 블로킹 모델로 싱글 스레드가 혼자서 일을 처리하지만    
> 들어오는 요청 순서가 아닌 논 블로킹 방식으로 이전 작업이 완료될 때까지 대기하지 않고 다음 작업을 수행한다.

**이벤트 루프**
> 비동기 처리가 필요하게 될 경우 libuv 라이브러리에서 제공하는 비동기 처리를 하게되는데, 이 때 libuv 라이브러리에서 제공하는게 **이벤트 루프**이다.    
> 이벤트 루프는 항상 루프(Loop)를 돌며 Call Stack(동기 작업이 순서대로 쌓이는 스택)과 Task Queue(비동기 작업이 끝나고 콜백을 호출하면 들어오는 큐)를 확인한다.   
> 그러다 Call Stack이 빈 상태가 되면, Task Queue에 있는 작업을 하나씩 Call Stack에 넣어준다.   
>   
> <img src="https://user-images.githubusercontent.com/83910753/138737515-2fea0b09-13d6-4033-8a46-c5b545862299.png" width="430" height="300">      <br>
> 이벤트 루프의 구성은 위와 같다. *각 단계별 자세한 설명은 [공식문서](https://nodejs.org/ko/docs/guides/event-loop-timers-and-nexttick/) 참고*


<br>

## Node.js 예상 질문
1. Node.js를 사용하는 이유는?   
> Node.js를 이용해 서버를 만들 수 있기 때문에 Client와 Server가 같은 언어를 사용해서 개발이 가능하다.   
> 싱글 스레드 기반의 비동기 논블로킹 모델을 사용하기 때문에 잦은 입출력 상황에서 속도가 빠르다.   
> NPM을 이용해 여러 라이브러리를 쉽게 사용할 수 있고 NVM을 이용한 버전 관리가 용이하다.   

2. Node.js는 어떻게 동작하는가?
> 순서대로 Call Stack에 작업이 쌓이다가 Call Stack에 비동기 작업이 들어오면 해당 작업을 백그라운드로 옮기고 나머지 작업을 진행한다.   
> 백그라운드에서 비동기 작업이 끝나면 해당 작업은 Task Queue에 들어가고 이벤트 루프의 판단하에 다시 콜스택에 넣어진다.   

3. 싱글스레드로 어떻게 Non-Blocking I/O 처리가 가능한가?
> 이벤트 기반의 비동기 처리로 가능하다.   
> 이벤트 루프에 의해 비동기 요청은 커널에서 작업을하고, 마치면 콜백 함수를 호출해 다시 이벤트 루프에 의해 스레드의 콜스택으로 돌아오는 방식이다.

4. Node.js의 단점은?
> 싱글 스레드이기 때문에 하나의 요청을 처리할 때 CPU 작업이 많아지면 다른요청이 지연된다.   

5. 브라우저와 Node.js의 (런타임으로서의) 차이점?
> 브라우저 : HTML, CSS, JS를 실행하여 브라우저를 랜더링하는 것이 주 목적. 비동기 처리시 Web API를 사용한다.   
> Node.js : JS의 서버 개발 환경을 제공하는 것이 주 목적. 비동기 처리시 커널을 사용한다.   

6. Node.js에서 콜백을 설명하세요.
> 콜백 함수는 주어진 작업 후에 호출되고 그 동안 다른 작업을 실행할 수 있다.    
> 비동기 플랫폼이기 때문에 Node.js는 콜백에 크게 의존하며, Node의 모든 API는 콜백을 지원하도록 작성되었다.

**< 추천 사이트 >**   
Node.js 기술면접 리스트 : [2021년 상위 48개 이상의 Node.js 인터뷰 질문과 답변](https://www.simplilearn.com/tutorials/nodejs-tutorial/nodejs-interview-questions)

<br>

## 그 외의 관련 개념
<details>
<summary>런타임</summary>
<div markdown="1">

> 프로그래밍 언어가 구동되는 환경
</div>
</details>

<details>
<summary>스레드</summary>
<div markdown="1">

> 프로그램 : 어떤 작업을 위해 실행할 수 있는 파일   
> 프로세스 : 메모리에 올라와 실행되고 있는 프로그램의 인스턴스   
> 스레드 : 프로세스가 할당받은 자원을 이용하는 실행의 단위
</div>
</details>

<details>
<summary>V8 엔진</summary>
<div markdown="1">

> 오픈소스로 구글에서 개발했다. C++로 작성되었으며, 구글 크롬과 Node.js에서 사용된다.    
> 인터프리터를 사용하지 않고 머신코드로 변환하기 때문에 속도가 빠르다.
</div>
</details>

<details>
<summary>이벤트</summary>
<div markdown="1">

> 말 그대로 *어떠한 사건이 발생한 것*    
> Node.js에서는 비동기적 작업이 들어온 것, 끝난 것 등이 됨
</div>
</details>

<details>
<summary>Blocking 과 Non-Blocking I/O</summary>
<div markdown="1">

> I/O : Input / Output. I/O 요청이 들어오면 시스템 콜을 보내고, 그 순간에 커널로 제어권이 넘어간다. (문맥 전환)   
> 유저 프로세스(혹은 스레드)는 제어권이 다시 돌아오기 전에는 Block 상태가 된다.   
### Blocking I/O
> 의미 : 하나의 프로세스가 어떤 자원을 사용하고자 할 때 그 자원을 다른 프로세스가 점유하고 있다면, 그 프로세스가 그 자원의 사용을 끝마칠 때까지 기다려야 한다는 것   
>    
> 멀티 스레드의 방식이 블로킹 I/O이다.   
> I/O 작업이 시작되면 응답이 돌아올 떄 까지 아무것도 하지 않고 시간을 낭비한다. (커널 입장에선 I/O 작업이 완료될 때까지 응답을 보내지 않는다.)   
> 이를 해결하기 위해 멀티 스레드로 보완하지만, 스케쥴링을 위한 처리시간과 문맥 전환으로 인해 네트워크에서 대규모 요청을 처리하기엔 부적절하다.   
> <img src="https://user-images.githubusercontent.com/83910753/138750001-208b27f7-d027-4f46-8ef2-7fe86ba09b4e.png" width="30%" height="30%">
>  [ 동기적 블로킹 모델 ]

### Non-Blocking I/O
> Node.js의 싱글 스레드 방식이다.   
> I/O 작업이 시작되면 I/O 작업 처리에 대한 응답을 기다리지 않고, 유저 프로세스(혹은 스레드)는 바로 다음 작업을 실행한다.   
> I/O 처리는 백그라운드에서 실행되다가, 완료되면 커널이 유저 프로세스에게 알려준다.   
> <img src="https://user-images.githubusercontent.com/83910753/138751253-145bf29a-755d-4505-813f-696bab18d4ff.png" width="30%" height="30%">
>  [ 비동기적 논블로킹 모델 ]

더 자세한 설명이나 대표적인 두가지 외의 비동기적 블로킹 모델, 동기적 논블로킹 모델(IBM에선 이 분류에 오류가 있다는 의견도 있다)은 아래 블로그 참조!    
[블로그](https://limdongjin.github.io/concepts/blocking-non-blocking-io.html#ibm-%E1%84%8B%E1%85%A1%E1%84%90%E1%85%B5%E1%84%8F%E1%85%B3%E1%86%AF)
</div>
</details>

<details>
<summary>Common JS</summary>
<div markdown="1">

> 모듈화를 위해 Node.js에서 사용하는 포맷. Node.js에서 사용하는 자바스크립트.   
> 가장 큰 차이점은 모듈 사용에 있는데, Common JS는 require(), module.export방식을 사용한다.
</div>
</details>

<details>
<summary>인터프리터언어, 컴파일언어, 스크립트언어</summary>
<div markdown="1">

> 인터프리터 언어 : 컴파일을 거쳐서 기계어로 변환되지 않고 바로 실행되는 프로그래밍 언어. 인터프리터가 한줄씩 해석해서 바로 명령어를 실행함. 👈 JS    
> 컴파일 언어 : 반드시 기계어로 컴파일 되어야만 실행시킬 수 있는 프로그래밍 언어    
> 스크립트 언어 : 응용 소프트웨어를 제어하기 위해 사용하는 프로그래밍 언어. 소스를 컴파일 하지 않고 인터프리터로 소스코드를 한줄한줄 읽어 바로 싱행하는 방식으로 동작. 👈 JS   
</div>
</details>

<details>
<summary>Task Queue</summary>
<div markdown="1">

> 매크로 태스크와 마이크로 태스크가 있다.   
> 이벤트 루프는 우선적으로 마이크로 태스크를 확인한다. 마이크로 태스크는 코드를 이용해서만 만들 수 있고 주로 프라미스를 이용해 만든다.   
> 매크로 태스크 하나를 처리한 후 다른 매크로 태스크나 랜더링 작업을 하기 전에 마이크로 태스크 큐에 있는 작업 전부를 처리한다.
</div>
</details>

<br>

## 참고 사이트
주오님 노션 [Node.js의 정의와 코어 컨셉](https://crawling-healer-570.notion.site/Node-js-9435c989169c4cc4b1643770ab94551b)   
Node.js에 대한 정리가 잘 되어있는 [블로그](https://hanamon.kr/nodejs-%EA%B0%9C%EB%85%90-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0/)   
[Blocking, Non-Blocking I/O에 대한 개념 설명](https://limdongjin.github.io/concepts/blocking-non-blocking-io.html#ibm-%E1%84%8B%E1%85%A1%E1%84%90%E1%85%B5%E1%84%8F%E1%85%B3%E1%86%AF)   
[Node.js는 백엔드만의 영역일까?](https://perfectacle.github.io/2017/06/18/what-is-node-js/)
