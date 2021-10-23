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

## 💎 리덕스 란? _redux
액션이라는 이벤트를 사용하여 애플리케이션 상태를 관리하고 업데이트하기 위한 상태관리 라이브러리로써, <br/>
리덕스 라이브러리는 예측가능한 방식으로만 업데이트될 수 있도록 보장하는 규칙과 함께 전체 애플리케이션에서 사용해야 하는 상태에 대한 ***중앙 저장소 같은 역할***을 한다.

## 💎 리덕스의 데이터 흐름 _redux-data-flow
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

## 💎 리덕스를 사용시 지켜야하는 필수규칙 _redux-required-rules

- 1. 하나의 애플리케이션 안에는 하나의 스토어만 사용하자는 원칙
- 2. 상태를 변화시키는 방법은 오직 액션을 일으키는 것, 상태를 변화시키는 의도를 정확하게 표현할 수 있고, 상태 변경에 대한 추적이 용이해지게 된다.
- 3. 변화를 일으키는 리듀서 함수는 순수한 함수여야 한다.
: 이전 상태와 액션 객체를 파라미터로 받고,
: 파라미터 외의 값에는 의존하면 안된다. 영향을 받지 않아야 한다.
: 이전 상태는 절대로 건드리지 않고, 변화를 준 새로운 상태 객체를 만들어서 반환한다.
: 똑같은 파라미터로 호출된 리듀서 함수는 언제나 똑같은 결과 값을 반환해야한다. 즉, 기본값 상태는 변하지 않아야 한다.

## 💎 리덕스를 사용해야 하는 이유? _Why Use Redux?

## 💎 리덕스의 특징 _redux-features

## 💎 리덕스의 장 * 단점 _redux-pros-and-cons

## 💎 mvc패턴 vs redux _mvc-pattern vs redux
