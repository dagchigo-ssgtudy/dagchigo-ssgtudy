# 💎 Redux

## CONTEXT
- [리덕스 란](#redux)
- [리덕스의 데이터 흐름](#redux-data-flow)
- [리덕스의 주요 용어 정리](#redux-principal-terms)
- [리덕스를 사용시 지켜야할 필수규칙](#redux-required-rules)
- [리덕스를 왜 사용해야 하는 이유?](#why-Use-Redux?)
- [리덕스의 특징](#redux-features)
- [리덕스의 장*단점](#redux-pros-and-cons)
- [mvc패턴 vs redux](#mvc-pattern-vs-redux)

## 💎 리덕스 란?_redux
액션이라는 이벤트를 사용하여 애플리케이션 상태를 관리하고 업데이트하기 위한 상태관리 라이브러리로써, <br/>
리덕스 라이브러리는 예측가능한 방식으로만 업데이트될 수 있도록 보장하는 규칙과 함께 전체 애플리케이션에서 사용해야 하는 상태에 대한 ***중앙 저장소 같은 역할***을 한다.

## 💎 리덕스의 데이터 흐름_redux-data-flow
![redux-data-flow](https://user-images.githubusercontent.com/80687195/138536932-21377ed9-1f55-42f7-96d9-2c9086f52962.gif)
<br />
### Redux의 데이터 흐름은 <br />
동일한 단방향으로 컴포넌트에서 ***dispatch***(store의 내장함수; store에서 주는 state바꾸는 함수)라는 함수를 통해 ***action***(디스페함수이름)이 발동되고 ***reducer***에 정의된 로직에 따라 store의 state가 변화하고 그 state를 쓰는 컴포넌트가 변하는 흐름을 따른다.

## 💎 리덕스의 주요 용어 정리 _redux-pricipal-terms

### Action(액션)
```js
{ type : GET_RECIPES_SUCCESS,
payload: recipes }
```
상태에 변화가 필요하다면 액션을 일으키며, 액션은 객체로 표현이 되고 type필드를 반드시 가지고 있어야하는 특징을 가진다.<br />
실생활에서 예를 든다면, 식당에서 음식 주문서와 같은 역할을 하는 거라고 보면 됩니다.<br />

### Action Creator(액션생성함수)
```js
function action creator () {
 
 //액션을 반환
 return {
   type: GET_RECIPES_SUCCESS,
   payload: recipes
 }
}
```
액션 객체를 만들어주는 함수입니다. <br />
식당에서 음식 주문을 넣는 자판기와 같은 역할을 하는 거라고 보면 됩니다. <br />

### Reducer
```js
const initialState = { recipes: [] }
function reducer (state = initialState, action) {
  switch(action.type) {
    case GET_RECIPES_SUCCESS:
      return {
        ...state,
        recipes: action.payload
      }
    default:
      return state
  }
}
```

현재 상태와 액션 객체를 받아, 필요하다면 새로운 상태를 리턴하는 함수 <br/>
액션 유형을 기반으로 이벤트를 처리하는 이벤트 리스너라고 생각하면 됩니다.<br/>
식당에선 음식주문에 따라 음식을 만들어서 음식을 내보내는 역할을 하는 거라고 보면 됩니다.<br/>

### Store
```js

import { createStore } from 'redux'

const initialState = { recipes: [] }
function reducer (state = initialState, action) {
  switch(action.type) {
    case GET_RECIPES_SUCCESS:
      return {
        ...state,
        recipes: action.payload
      }
    default:
      return state
  }
}

const store = createStore(reducer)

```

스토어에는 상태가 들어있습니다. <br/>
모든 애플리케이션에 있는 상태를 저장한다면 하나의 스토어에서 모든 상태를 관리할 수 있게 되어지는 것이다. <br/>

### Dispatch

```js

store.dispatch({ type: GET_RECIPES_SUCCESS })

```

스토어의 내장 함수 중 하나이며, 액션 객체를 넘겨줘서 상태를 업데이트하는 유일한 방법으로, 이벤트 트리거(event trigger)이라고 보면 됩니다.
react-hooks useDispatch를 사용하여 dispatch하는 것도 가능합니다.
식당에서 직원이 음식 주문을 받아 주방에 주문서를 전달하는 거라고 보면 됩니다. <br/>

### Selector

이 또한 스토어의 내장함수인 getState를 사용하여 상태 값을 가져올 때 사용합니다.<br/>
react-hooks useSelector를 사용하여 가져오는 것도 가능합니다.

### Redux-thunk(middleware)

```js

import thunk from 'redux-thunk';
import { createStore, applyMiddleware } from 'redux';

const initialState = { recipes: [] }
function reducer (state = initialState, action) {
  switch(action.type) {
    case GET_RECIPES_SUCCESS:
      return {
        ...state,
        recipes: action.payload
      }
    default:
      return state
  }
}

const middleware = [thunk]
const store = createStore(reducer, applyMiddleware(...middleware))

```
액션 안에 api를 호출하게 되면 비동기적으로 일어날 수 있도록 도와주는 Middleware함수입니다. <br/>
보통 리덕스에서 미들웨어를 사용하는 주된 사용 용도는 비동기 작업을 처리할 때 사용하는데, 리액트 앱에서 우리가 만약 백앤드 api를 연동해야 된다면, 리덕스 미들웨어를 사용하여 처리해야 하곤 합니다. <br />
redux의 액션들은 모두 동기적으로 이러나기 때문에 중간에 비동기적 처리해야하는 처리가 있다면 에러가 나게 됩니다. 이런 경우를 대비하여 redux middleware를 사용하여 처리해 줍니다. 중간과정에서 비동기를 처리를 해준 다음 액션을 리듀서로 전달해주는 역할을 합니다.

![ReduxAsyncDataFlowDiagram-d97ff38a0f4da0f327163170ccc13e80](https://user-images.githubusercontent.com/80687195/138538814-9f206b8e-44f7-4f18-8140-a0faf649ad96.gif)

## 💎 리덕스를 사용시 지켜야하는 필수규칙_redux-required-rules

- 하나의 애플리케이션 안에는 하나의 스토어만 사용하자는 원칙
- 상태를 변화시키는 방법은 오직 액션을 일으키는 것, 상태를 변화시키는 의도를 정확하게 표현할 수 있고, 상태 변경에 대한 추적이 용이해지게 됩니다.
- 변화를 일으키는 리듀서 함수는 순수한 함수여야 합니다. <br/>
: 이전 상태와 액션 객체를 파라미터로 받아야 합니다 <br />
: 파라미터 외의 값에는 의존하면 안된다. 영향을 받지 않아야 합니다.<br />
: 이전 상태는 절대로 건드리지 않고, 변화를 준 새로운 상태 객체를 만들어서 반환해야 합니다. <br />
: 똑같은 파라미터로 호출된 리듀서 함수는 언제나 똑같은 결과 값을 반환해야 합니다. 즉, 기본값 상태는 변하지 않아야 합니다. <br/>

## 💎 리덕스의 특징_redux-features
- 하나의 상태를 낳는다, 즉 하나의 객체 안에 애플리케이션에서 필요한 모든 데이터를 우깨워 넣으며 저렇게 한 곳에 데이터를 중앙 집중적으로 관리하면 아무리 여러 곳에 흩어져 있는 것보다 훨씬 더 데이터를 관리 하기가 쉬워집니다. 단 하나의 스테이트를 유지하는 걸 통해서 애플리케이션의 복잡성을 낮춥니다

- 데이터의 상태변화를 직접 하지못합니다. 디스펙쳐라는 걸 통해서 또 리듀서를 통해서만 데이터의 수정을 가할 수 있습니다. 데이터를 가져올 때 직접 가져오지 못합니다. getState라는 함수를 통해서 가져올 수 있습니다. 데이터를 외부에서 직접적으로 제어할 수 없도록 하는 걸 통해서 의도하지 않게 얘기치 않게 스테이트값이 바뀌는 문제를 사전에 차단하는 걸 통해서 우리 애플리케이션을 보다 예측 가능하게 만드는 것 입니다.

- 그리고 각가의 스테이트값들을 생성할 때 철저하게 통제하고 데이터를 바꿀 대 원본을 바꾸는 것이 아니라 복제하고 복제한 데이터를 수정해서 그것을 새로운 원본으로 만드는 이런 방법을 채택하고 있습니다. 각각의 상태의 변화가 서로에게 영향을 전혀 주지 않는 독립된 형태를 유지할 수 있고 이러한 특징을 잘 이용하면 언도와 리드와 같이 애플로케이션의 상태를 바꾸는 것은 매우 쉽게 처리할 수 있습니다.

- 리덕스를 이용하게 되면 현재 상태 뿐만 아니라 이전의 상태까지 꼼꼼하게 코딩하는 걸 통해서 과거에 어느 시점으로 돌아가서 그 시점에서 이 애플리케이션의 상태가 무엇인가를 찾아내는 걸 통해서 문제해결을 훨씬 더 쉽게 할 수 있도록 도와줍니다.

## 💎 리덕스의 장 * 단점_redux-pros-and-cons
### 🌝 장점

- 우리의 코드가 어떤 결과를 가져올지 예측 가능하게 만들어주며 한눈에 보기 쉽게 만들어줍니다.
- 전역으로 사용이 가능합니다. 
- 상태끌어올리기보다 효율적이고 짧은 코드를 작성하여 복잡한 코드를 좀더 간략하고 효율적으로 작성이 가능하게 해줍니다. 즉, A,B,C,D컴포넌트가 있다고 가정했을 때 A에서 D컴포넌트에 접근해 무언가 하려고 한다면  A,B,C,D순서로 접근 후 다시 D,C,B,A루트를 통해 돌아와야 합니다. 이때 하나의 스토어 (Store)라는 매체를 두면 위의 순서가 아닌 A>store>D식의 효율적인 접근이 가능하게 해줍니다.

### 🌚 단점
- 반복적은 코드를 써야합니다.
- 반복적은 코드를 써야함에 코드양이 많아 집니다.

## 💎 리덕스를 사용해야 하는 이유?_Why Use Redux?
- 상태 예측 가능하게 만들수 있다.
- 유지 보수가 비교적 쉬워진다
- 의도하지 않게 스테이트 값이 바뀌는것을 사전에 차단할 수 있다.

## 💎 mvc패턴 vs redux_mvc-pattern vs redux

### mvc패턴이란
MVC는 model-view-controller의 약자

개발 할 때, 3가지 형태로 역할을 나누어 개발하는 방법론입니다.

비지니스 처리 로직과 사용자 인터페이스 요소들을 분리시켜 서로 영향없이 개발 하기 수월하다는 장점이 있습니다.

### Model 
어플리케이션이 ***"무엇"*** 을 할 것인지를 정의한다. 내부 비지니스 로직을 처리하기 위한 역할을 할 것이다.

### Controller 
모델이 ***"어떻게"*** 처리할 지를 알려주는 역할을 할 것입니다. 화면의 로직처리 부분입니다. 화면에서 사용자의 요청을 받아서 처리되는 부분을 구현되게 되며, 요청 내용을 분석해서 Model과 View에 업데이트 요청을 하게 됩니다. 

### View 
화면에 ***"무엇"*** 인가를 "보여주는 위한 역할"을 합니다. 컨트롤러 하위에 종속되어, 모델이나 컨트롤러가 보여주려고 하는 모든 필요한 것들을 보여줄 것이다. 최종 사용자에게 "무엇"을 화면(UI)으로 보여줌" 

### MVC의 한계
MVC에서 view는 controller에 연결되어 화면을 구성하는 단위요소이므로 다수의 view들을 가질 수 있습니다. 그리고 Model은 Controller를 통해서 view와 연결되어지지만, 이렇게 Controller를 통해서 하나의 view에 연결될 수 있는 model도 여러개의 될 수 있습니다. 
즉, 뷰와 모델이 서로 의존설을 띄게 됩니다. 화면에 복잡한 화면과 데이터의 구성 필요한 구성이라면, controller에 다수의 model과 view가 복잡하게 연결되어 있는 상황이 생길 수 있습니다. 
MVC가 너무 복잡하고 비대해져서, 새 기능을 추가할때마다 크고 작은 문제점을 가지고 소스 분석이나 테스트도 어렵습니다. 

![mvc패턴](https://user-images.githubusercontent.com/80687195/138582235-423e3685-8201-49bd-a408-5eeec3f6b8e7.png)

![mvc](https://user-images.githubusercontent.com/80687195/138582352-0d378010-9997-44d3-818d-665da546abba.png)

한계를 극복하기 위한 해결책으로 ***단방향 데이터 흐름*** 입니다. 단방향으로만 흐르고, 새로운 데이터를 넣으면 처음부터 흐름이 다시 시작되는 방식으로 설계되었고, 이 시스템 구성 즉, 아키텍처를 flux라고 불렸습니다. 

### Flux 패턴
<img width="755" alt="flux_with_action" src="https://user-images.githubusercontent.com/80687195/138582759-0462a22f-13ae-43b5-86d2-f5d8f8277119.png">


Model이 view를 반영하고, view가 model을 변경하는 양방향 데이터 흐름에서 벗어나 단방향으로만 데이터를 변경할 수 있도록 만든거입니다.

### Redux
redux는 flux패턴을 구현한 라이브러리라고 생각하면 됩니다. 기본적인 원리는 flux패턴과 거의 비슷하다고 볼 수 있겠습니다. 

단지 ***차이점***
data처리를 reducer라는 놈이 할 뿐입니다. flux패턴에서 언급한 dispatch에 등록된 callback정도로 이해하면 되겠습니다. <br/>
action => dispatch => reducer => store, store변경 시 view에 data변경됬다고 알려줍니다.

