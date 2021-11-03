# EventLoop

EventLoop가 조사를 해보니까 간단하게 한줄 설명이나 짧게 설명 할 수 없는 내용입니다.<br/>
왜냐면은 굉장히 여러가지 개념들이 종합해서 들어가기 때문입니다.<br/>
개념을 정의하기보단 진행 과정을 보여드리면서 설명하겠습니다.<br/>

## Single Thread
스레드(thread)는 어떠한 프로그램 내에서, 특히 프로세스 내에서 실행되는 흐름의 단위를 말합니다.<br/>
이벤트 루프를 알아보기 위해서 가장 먼저 설명드릴 것은<br/>
자바스크립트의 큰 특징 중 하나가 'Single Thread' 기반의 언어라는 점입니다.<br/>
스레드가 하나라는 말은 동시에 하나의 작업만을 처리할 수 있다는 말이 되죠.<br/>
하지만 실제로 자바스크립트가 사용되는 환경을 생각해 보면 많은 작업이 동시에 처리되고 있는 걸 볼 수 있습니다.<br/>
예를 들면, 웹브라우저는 http 요청이 진행되면서 다른 함수가 작동하는 걸 많이 봐왔죠,<br/>
Node.js에서는 동시에 여러 개의 HTTP 요청을 처리하기도 합니다.<br/>

## JS Engine

![1_pjRSYsfW-D8MCrGh9LS_4Q](https://user-images.githubusercontent.com/81761175/139897871-5ba64dcd-4d45-46d3-983f-7f60e30f23c7.png)

이제 자바스크립트의 문맥을 훑어보면서 함께 EventLoop에 대해서 알아보도록 합시다.<br/>
그림에서 JS는 자바스크립트 Engine을 뜻 합니다.<br/>
JS의 Engine중 가장 유명한 것이 구글의 크롬 V8 Engine입니다.<br/>
이 엔진 내부에는 Memory Heap 과 Call Stack 으로 구성되어 있습니다.<br/>

![Screenshot from 2021-11-01 21-16-15](https://user-images.githubusercontent.com/81761175/139872528-92581a63-8d62-4076-b95a-acb7dbbf978d.png)

### Memory Heap

Memory Heap 은 프로그래밍을 할 때 선언된 변수, 함수가 담겨지는 메모리 할당이 일어나는 곳입니다.<br/>
한마디로 메모리 저장소입니다.<br/>
JS Engine은 코드를 실행 할 때 변수와 함수를 만난다면 그 값을 이 Memory Heap에서 찾게 됩니다.<br/>

### Call Stack

call stack은 자바스크립트에서 코드가 실행될 때 쌓이는 곳 이고 stack의 형태로<br/>
Last In First Out 즉 마지막에 들어온게 먼저 나가는 구조입니다.<br/>
함수를 실행하게 되면 우선 stack에 쌓인뒤 코드를 읽고 return 되면서 함수가 종료가 되는것입니다.<br/>
여기서 `call stack이 비었다`는 말을 설명 해놔야 합니다. 이 말은 더 이상 실행을 할 함수가 없다는 것을 의미합니다.<br/>
이 자바스크립트에서 call stack은 여러 개가 없고 하나밖에 없습니다.<br/>
왜냐면 자바스크립트는 single thread 단일 스레드 프로그래밍 언어이기 때문입니다.<br/>


### Callback Function (부가적인 개념)
- 다른 함수의 인자로 넘겨지는 함수<br/>
- 콜백 수신 함수에 의해 특정 시점에 실행<br/>
- 동기 콜백의 경우 호출 즉시 실행<br/>
- 비동기 콜백의 경우 나중에 조건을 만족했을때 실행<br/>
- 이벤트 리스너<br/>
- 타이머 / XMLHttpRequest 요청<br/>

![Screenshot from 2021-11-02 23-55-13](https://user-images.githubusercontent.com/81761175/139873460-f5ecf4e6-fcfb-49a3-b95c-2db10d5288e9.png)

예시에서는 전역 함수 test가 있고 그 내부에서 test2와 test1을 선언합니다.<br/>
test1에서는 test2함수를 실행시켜준 뒤, 콘솔을 반환합니다.<br/>
이 코드를 실행하게 될 때 실행 순서는 쌓이는 과정을 영상으로 보여드리겠습니다.<br/>

https://user-images.githubusercontent.com/81761175/139883267-4d928dce-372e-4fea-a0b3-0a110c85d85f.mp4

1. test가 메인으로 먼저 쌓인다. <br/>
2. test1이 실행되어 test 위로 쌓이게 된다.<br/>
3. test2가 실행되어 test1 위로 쌓이게 된다.<br/>
4. test2 내부의 console이 위로 쌓여 실행된다. (test2, 4)<br/>
5. 더 이상 실행할 코드가 없으니 test2가 return 된다.<br/>
6. test1 내부에 console이 위로 쌓여 실행된다.(test1, 2)<br/>
7. 더 이상 실행할 코드가 없으니 test1이 return 된다.<br/>
8. test 내부의 console이 위로 쌓여 실행된다.(test3, 6)<br/>

![Screenshot from 2021-11-02 01-12-52](https://user-images.githubusercontent.com/81761175/139893352-3540835a-3c20-4086-8a9a-14c1590c1a87.png)

아까 자바스크립트가 Single Thread 언어라고 말씀을 드렸는데<br/>
금방 말씀드렸다시피 Call stack을 하나만 사용합니다.<br/>
그리고 동시에 한 가지 일만 처리할 수 있다는 뜻이죠.<br/>
근데 함수가 실행되는 호출 스택이 한 개면서 어떻게 비동기 요청을 지원하고 동시성에 대한 처리는 누가 하는 걸까요?<br/>

![Screenshot from 2021-11-02 00-23-27](https://user-images.githubusercontent.com/81761175/139894017-e5ef23fa-db3b-44fb-af84-03ff3630aae9.png)

일단 자바스크립트 엔진이 코드를 진행하다가 중간에 비동기 코드를 만나면 이 코드를 자바스크립트 뒤편에서 실행을 하게 됩니다.<br/>
그다음은 나머지 코드를 진행해서 이 비동기 코드는 자바스크립트 뒤편에서 실행이 되도록 놔두는 거죠<br/>

![1_pjRSYsfW-D8MCrGh9LS_4Q](https://user-images.githubusercontent.com/81761175/139897871-5ba64dcd-4d45-46d3-983f-7f60e30f23c7.png)

여기서 시야를 좀 더 넓혀서 금방 말씀드린 뒤편인 웹 브라우저에 대해서 봐야 합니다.<br/>

웹 브라우저는 자바스크립트 엔진 말고도 web api 콜백 큐 이벤트 루프 이런 것들을 가지고 있습니다.<br/>
우리가 자주 사용하는 http 요청 dom 메 서드 setTimeout 등은 모두 web API에서 제공하는 메서드 들인데요.<br/>
이 메서드들은 비동기 메서드이기 때문에 작동을 마치면 콜백 함수를 콜백 큐에 집어넣습니다.<br/>
이 콜백 큐는 다른 말로 task queue라고 합니다.<br/>
콜백 큐에 들어간 콜백 함수들은 순차적으로 실행을 대기합니다.<br/>

이렇게 자바스크립트 엔진 자체는 Single Thread지만, <br/>
실제로 자바스크립트가 구동되는 환경인 웹 브라우저에는 여러 개의 Thread가 사용됩니다.<br/>
조금 더 자세히 말하자면 web api가 Multi Thread로 동작하는 거죠<br/>
자바스크립트가 web api와 상호 연동을 하기 위해서 필요한 장치가 Callback Queue와 EventLoop입니다.<br/>

## WebAPI & Callback Queue & EventLoop 동작 과정

또 예시 코드를 통해 앞서 설명드린 부분에 대해 보여드리겠습니다.<br/>

![Screenshot from 2021-11-03 01-07-16](https://user-images.githubusercontent.com/81761175/139903979-9ed104a2-d22b-428c-87fe-04b44b5df18d.png)

해당 코드가 실행이 되면 우선은 call stack에 first 함수가 들어가게 되고 1+1 console이 실행이 됩니다.<br/>
그다음에 second 함수가 실행이 되고, setTimeout이 실행이 됩니다.<br/>
아까 전에 setTimeout은 Web API에서 실행이 된다고 했었죠.<br/>
그래서 첫 번째 인자로 들어간 콜백 함수를 가지고 있는 타이머를 webAPI에서 생성하게 됩니다.<br/>
이 타이머를 생성하는 걸로 setTimeout의 역할은 끝이 나고 callstack에서 return됩니다.<br/>
그리고 이제 second 함수가 return되겠죠 그다음에 3+3 console이 출력되고 first 함수도 pop을 하게 됩니다.<br/>

이제 web api에 있는 타이머만 남은 상태인데<br/>
타이머가 정해진 시간을 모두 세고 나면 콜백 함수를 callback queue에 넣고 자기는 사라집니다.<br/>
그러면 이 콜백은 callback queue에서 실행되기를 기다리게 되겠죠<br/>
이 콜백 함수도 결국엔 함수이기 때문에 call stack에 들어가야 합니다.<br/>

https://user-images.githubusercontent.com/81761175/139905418-68ad3fbd-25cd-41b6-8809-c03157a5d2a8.mp4

## 여기서부터 핵심입니다. 중요!
이때 이제 드디어 이벤트 루프가 여기서 동작을 하게 됩니다,<br/>

이벤트 루프는 이 전체 시스템에서 아주 단순한 일을 하는 작은 파트인데,<br/>
이 이벤트 루프는 call stack과 callback queue를 계속 주시하고 있습니다.<br/>
call stack이 비어 있으면, 먼저 들어온 순서대로 callvack queue에 있는 콜백 함수들을 callstack으로 집어넣습니다.<br/>

callback queue를 지켜보다가 `콜백 함수가 왔네?` 하고 `call stack 이 비어있네?`이러면<br/>
콜백 함수를 call stack으로 옮겨주는 게 EventLoop입니다.<br/>

이때 call stack이 반드시 비어있어야만 callback queue에 callback 함수가 call stack으로 옮겨진다는 사실 잊지 마시기 바랍니다.<br/>

first 함수까지 모두 실행이 되어서 callstack이 비어있으니 이벤트 루프가 콜백 함수를 call stack으로 옮겨주고 2+2 console을 실행시킨 뒤 return됩니다.<br/>

자바스크립트에서 비동기 요청을 할 때에는 이 webapi에서 따로 처리를 해주기 때문에<br/>
ajax 요청이라든지 하던 중 다른 일을 할 수 있는 것입니다.<br/>

## 한 번 더 확인해 봅시다.

이제 이벤트 루프가 어떻게 동작하는지 살펴보았으니 한 가지 사실을 더 알려드리면서 다시 한번 보겠습니다.<br/>

![Screenshot from 2021-11-03 01-23-38](https://user-images.githubusercontent.com/81761175/139905192-206edccb-96b3-400e-86fe-8f0ac51d40cb.png)

아까와 똑같은 코드입니다.<br/>
근데 이번에는 setTimeout의 타이머가 0이죠,<br/>
이렇게 타이머를 0으로 설정하고 코드를 실행한다면 어떻게 될까요<br/>
뭔가 타이머가 0이니까 1+1 2+2 3+3 순으로 실행될 거 같죠?<br/>
하지만 실제로 실행시켜보면 아까와 똑같습니다.<br/>

https://user-images.githubusercontent.com/81761175/139905713-2a0f5f4a-911a-4ef9-8abe-2c9fa4a61b24.mp4

우선은 call stack에 first 함수가 들어가게 되고 1+1 console이 실행이 됩니다.<br/>
그다음에 second 함수가 실행이 되고, setTimeout이 실행이 됩니다.<br/>
여기서 이 setTimeout부터 말씀을 드릴게요<br/>
setTimeout의 타이머는 0 이긴 하지만 그래도 webAPI에 타이머가 생성이 됩니다.<br/>
여기서 타이머가 동작합니다. 0이니까 바로 callback queue에 들어가겠네요<br/>

그리고 아까 말씀드렸듯이 callstack이 비어있어야 EventLoop가 콜백 함수를 옮긴다고 하였죠.<br/>
다시 callstack으로 가보겠습니다.<br/>
이제 second 함수가 return되겠죠 그다음에 3+3 console이 출력되고 first 함수도 pop을 하게 됩니다.<br/>
그러면 그제서야 이벤트 루프는 이 callback 함수를 callstack에 옮고 실행이 2+2 console이 실행이 되는 겁니다.<br/>

# 정리

1. Event Loop는 Call Stack과 Callback Queue의 상태를 체크하여,<br/>
   Call Stack이 빈 상태가 되면, Callback Queue의 첫 번째 콜백을 Call Stack으로 밀어 넣어줍니다.<br/>
   이러한 반복적인 행동을 틱(tick)이라 부릅니다.<br/>
  
2. 자바스크립트는 Single Thread 프로그래밍 언어라 한 번에 하나씩 밖에 실행할 수 없지만,<br/>
   Web API, Callback Queue, Event Loop 덕분에 멀티 스레드처럼 동시성을 지니고 있는 겁니다.<br/>
   
3. setTimeOut의 타이머가 0이어도 Call Stack이 비었을 때 실행이 되기 때문에 가장 마지막에 실행됩니다.<br/>
   그 이유는 Web API의 메서드라서 Callback Queue를 거치기 때문입니다.<br/>


