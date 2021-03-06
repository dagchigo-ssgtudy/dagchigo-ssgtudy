# MVC의 등장 배경
- 디자인 패턴이 정립되기 전 개발자들은 개발을 하면서 코드량이 많아지고 구조가 복잡해짐에 따라 기능을 추가하거나 수정할 때 많은 어려움을 겪었음
- 하나의 기능만 추가/수정 하기 위해 전체 코드를 수정해야 하는 상황이 생김(유지 보수의 어려움)
- 시간이 지나 유지 보수에 편한 코드 패턴이나 규칙들이 정립됨
- MVC → 어떻게 하면 유지 보수를 편하게 할 수 있을까? 하는 고민이 쌓여 탄생한 디자인 패턴 중 하나  

### * 유지보수가 편한 코드란?
- 특정 기능을 추가/수정 할 때 되도록이면 최소한의 코드만 수정해서 기능을 변경할 수 있는 코드
- 최소한의 코드만 수정해서 기능을 변경하려면?  
  → **변하는 것과 변하지 않는 것을 분리**해야 함(MVC가 아니더라도 모든 디자인 패턴들의 핵심)

# MVC 디자인 패턴이란?
- Model, View, Controller의 약자
- 소프트웨어를 설계하는 디자인 패턴 중 하나
- 프로젝트의 구성 요소를 3가지 역할로 구분한 패턴
  - Model : 데이터와 비즈니스 로직을 관리
  - View : 레이아웃과 화면을 처리
  - Controller : 명령을 Model과 View 부분으로 라우팅, 중간에서 로직을 제어  
- 사용자가 Controller를 통해 정보 요청  
- Controller는 Model을 조작하여 데이터를 받음  
- Controller는 Model로부터 받은 데이터를 시각적인 표현을 담당하는 View에게 보냄  
- View는 사용자에게 요청한 데이터를 보여줌  
<img src="https://user-images.githubusercontent.com/83861190/139564571-42b72561-9719-401b-a9cd-2d295eb410a3.jpg" width="500" height="400" />  

## Model
- 애플리케이션의 데이터(데이터베이스, 상수, 변수, 초기화값 등)를 나타냄
- 데이터의 가공을 책임지는 컴포넌트  

### * Model의 규칙
#### 1. 사용자가 편집하길 원하는 모든 데이터를 가지고 있어야 함
  - 화면 안의 박스에 글자가 표현된다면, 박스의 위치, 크기, 글자내용 등의 정보를 가지고 있어야 함    
#### 2. 뷰나 컨트롤러에 대해 어떤 정보도 알지 말아야 함
  - 데이터 변경이 일어났을 때 Model 내부에서 화면 UI를 직접 수정하는 등의 역할을 하면 안 됨(View의 영역과 겹치면 구분한 의미가 없음)    
#### 3. 변경이 일어나면, 변경 통지에 대한 처리 방법을 구현해야 함  
  ex) 텍스트 정보가 변경 → 이벤트를 발생시켜 누군가에게 전달해야 함  
  Model은 재사용 가능해야 하며 다른 인터페이스에서도 변하지 않아야 함

## View
- 사용자 인터페이스 요소를 나타냄(input텍스트, 체크박스 등)
- 데이터 및 객체의 입력/출력을 담당
- 사용자들이 볼 수 있는 화면

### * View의 규칙
#### 1. Model이 가지고 있는 정보를 따로 저장해서는 안 됨  
  - 모델로부터 정보를 받아서 화면에 표시하는 경우 화면에 표시만 하고 그 정보를 저장해서는 안 됨
#### 2. 모델이나 컨트롤러와 같은 다른 구성 요소들을 몰라야 함  
  - 자기 자신의 역할 외에 다른 요소를 참조하면 안 됨(뷰는 오직 화면에 데이터를 표시해주는 역할만 가짐)
#### 3. 변경이 일어나면, 변경 통지에 대한 처리 방법을 구현해야 함  
  ex) 화면 정보가 변경 → 이벤트를 발생시켜 누군가에게 전달해야 함
  View역시 재사용 가능해야 하며 다른 인터페이스에서도 변하지 않아야 함

## Controller
- 데이터와 사용자 인터페이스 요소를 잇는 다리 역할
- 사용자가 데이터를 클릭/수정 하는 등의 **이벤트**를 처리

### * Controller의 규칙
#### 1. 모델이나 뷰에 대해서 알고 있어야 함  
  - 모델과 뷰는 서로의 존재를 모르며, 변경을 외부에 알리고, 수신하는 역할
  - 컨트롤러는 이들을 중재하는 역할이기 때문에 알아야 함
#### 2. 모델이나 뷰의 변경을 모니터링 해야 함  
  - 애플리케이션의 메인 로직은 컨트롤러가 담당
  - 모델과 뷰의 변경을 통지받으면 이를 해석해서 각각의 구성 요소에게 통지해야 함  

# MVC 패턴을 사용하는 이유
- 서로 주어진 역할만을 담당하기 때문에 코드 유지 보수에 편리
- 애플리케이션의 확장성, 유연성을 높임
- 중복 코드 감소, 코드 재사용 용이  

# MVC의 한계점
- MVC의 특징 : **양방향 데이터 흐름**
- 컨트롤러 → 모델의 데이터 조회/업데이트 → 뷰에서 화면에 반영 → 뷰가 모델을 업데이트할 수도 있음 → 업데이트 된 모델이 다른 뷰에도 영향 줄 수 있음
- 복잡하지 않은 애플리케이션에서는 큰 문제x
- 애플리케이션이 커지면서 시스템 복잡도가 크게 증가  
  ex) View가 다양한 상호작용을 위해 여러 Model을 동시에 업데이트 할 경우  
  → 예측 불가능한 버그들이 생길 수 있음  

![MVC단점](https://user-images.githubusercontent.com/83861190/139565127-a2442466-eff6-4cf2-981a-9f931ba76be8.png)
## 사례) Facebook의 알림 버그
- 로그인 후 알림을 클릭해도 아무런 메시지가 없음
- 버그 수정 후에도 차후 다른 업데이트를 하다보면 다시 알림 버그 발생
- MVC의 양방향 데이터 흐름 → 예측 불가능한 버그 발생  
![facebook](https://user-images.githubusercontent.com/83861190/139565172-2c8117dc-4487-470a-aa2b-a58f4c42d7d2.png)

# Flux 디자인 패턴
- MVC패턴의 단점을 보완하기 위해 페이스북에서 개발한 아키텍쳐
- **단방향 데이터 흐름**
- Dispatcher, Store, View 세 부분으로 구성
- 데이터의 흐름 : Dispatcher → Store → View(Action을 통해 다시 Dispatcher로 흐름)
- 데이터의 변화를 예측하기 쉽게 함

![Flux](https://user-images.githubusercontent.com/83861190/139570552-1ae325d6-f60b-44f1-a3d4-d508bf376900.png)  

## Action
- View에서 사용자 상호작용 시 발생
- Dispatcher에서 콜백 함수가 실행되면 Store가 업데이트
- 콜백 함수가 실행될 시 데이터가 담겨있는 객체가 인수로 전달되어야 함
- 여기서 전달 되는 객체를 Action
- 액션 생성자(Action Creator) : Type과 데이터(Payload)로 구성

## Dispatcher
- Flux의 모든 데이터 흐름을 관리하는 허브 역할
- Action이 발생하면 Dispatcher로 전달
- Action Type에 대한 맞춤 콜백이 존재
- Dispatcher는 전달된 Action을 보고 등록된 콜백 함수를 실행하여 Store에 데이터를 전달

## Store
- 애플리케이션의 모든 상태 변경은 Store에 의해 결정
- Store는 변경된 데이터를 View에 전달
- 자신의 컴포넌트 트리에 속해있는 자식 노드 모두를 다시 랜더링 시킴

## View
- 화면에 데이터를 보여줌
- Flux의 View는 자식 View로 데이터를 흘려 보내는 Controller의 역할도 함(컨트롤러 뷰 라고도 함)

# MVC vs Flux
- 둘 다 유지 보수를 편하게 하기 위해 고안된 디자인 패턴
- MVC : 양방향 데이터 흐름
- Flux : 단방향 데이터 흐름

