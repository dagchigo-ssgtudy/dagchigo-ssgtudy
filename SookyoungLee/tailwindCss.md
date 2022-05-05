#🌪 Tailwind

## 테일윈드란?

Utility-First 컨셉을 가진, 인라인 스타일을 사용하는 CSS 프레임워크.

부트스트랩과 비슷하게 `m-1`, `flex` 와 같이 미리 세팅된 유틸리티 클래스를 활용하는 방식으로, HTML 코드 내에서 스타일링을 할 수 있다.

---

## 설치방법

How to install Tailwind ?
Link to 👉🏼 [Install Tailwind CSS with Create React App - Tailwind CSS](https://tailwindcss.com/docs/guides/create-react-app)

---

## 특징

- 쉽고 빠른 스타일링
- 일관된 디자인 시스템
- 좋은 사용자 경험으로 사용성 증가추세
  - [GitHub](http://github.com/)
  - [Nuxt.js](https://nuxtjs.org/)

<img width="1348" alt="스크린샷 2022-05-05 오후 12 58 21" src="https://user-images.githubusercontent.com/80618616/166866217-5a806230-2faa-4e8e-a026-d234d3b00dc1.png">

<img width="1348" alt="스크린샷 2022-05-05 오후 1 00 23" src="https://user-images.githubusercontent.com/80618616/166866259-68715d5d-cebf-44a1-863f-2fb0b515766c.png">

---

## 👍🏼 Tailwind CSS의 장점

### 1. Utility-First의 편리함과 빠른 개발

스타일 코드도 HTML 코드 안에 있기 때문에 HTML와 CSS 파일을 별도로 관리할 필요가 없다.

##### ✔️ HTML-CSS를 왔다갔다 하거나 화면을 분할해서 사용하지 않아도 된다.

##### ✔️ 태그의 스타일을 변경하기 위해 클래스명을 검색해가며 일일이 필요한 CSS 코드를 찾지 않아도 된다.

##### ✔️ styled-component 처럼 작은 스타일 변경에도 컴포넌트를 만들어야 하는 번거로움을 줄인다.

##### ✔️ 매번 클래스명을 짓지 않아도 된다.

- BEM, OOCSS 등의 방법론이 나올 정도로 클래스명 짓는 일은 까다롭다.
  Tailwind CSS를 사용하면 랩핑 태그의 클래스명을 사용할 일이 거의 없으므로 `container`, `wrapper`, `inner-wrapper`와 같은 클래스명을 고민하지 않아도 된다.

Link to 👉🏼 [CSS방법론 : OOCSS, BEM, SMACSS 비교해보기](https://whales.tistory.com/33)

### 2.**일관된 디자인**

모든 곳에서 동일한 색상이나 사이즈, 간격 등의 유틸리티 클래스를 사용 하므로 일관된 스타일로 구현할 수 있다.

<img width="768" alt="스크린샷 2022-05-05 오후 1 33 57" src="https://user-images.githubusercontent.com/80618616/166866420-761f9e77-0cfb-4e91-b4f5-cee2bf38c892.png">

### 3. **쉬운 반응형 페이지 및 커스터마이징**

다른 프레임워크들에 비해 기본 스타일 값을 디테일한 부분까지 쉽게 커스텀이 가능하다.

커스텀을 할 때 기본 스타일 값을 수정하는 방식이기에 디자인 일관성도 해치지 않는다.

반응형또한 제공해주고 있어 별도로 미디어쿼리를 적용하지 않아도 인라인스타일로 쉽게 지정할 수 있다.

<img width="427" alt="스크린샷 2022-05-05 오후 1 31 21" src="https://user-images.githubusercontent.com/80618616/166866470-34e6415d-c4c2-4987-8f84-769386add0d4.png">

중복되는 스타일은 @apply 로 지정하여 전역에서 지정한 클래스네임으로 동일한 스타일을 지정할 수 있음.

<img width="765" alt="스크린샷 2022-05-05 오후 1 38 33" src="https://user-images.githubusercontent.com/80618616/166866510-8d29fae8-6984-44e9-b7eb-16e65679c824.png">

### 4. \***\*Tailwind CSS IntelliSense\*\***

Tailwind CSS IntelliSense 익스텐션으로 자동완성 가능

<img width="632" alt="스크린샷 2022-05-01 오후 3 49 34" src="https://user-images.githubusercontent.com/80618616/166866543-96859508-4ea2-41d7-aab8-fe0f77e1e39b.png">

<img width="775" alt="스크린샷 2022-05-05 오후 1 32 46" src="https://user-images.githubusercontent.com/80618616/166866347-b74f4e0a-4a08-445f-8880-a23b2e28dcd3.png">

### JavaScript 코드와의 분리

Tailwind CSS는 JavaScript 코드와 완전히 분리되어 있다. 그러므로 프로젝트 진행 도중 JavaScript 프레임워크를 변경하여도 큰 추가 작업 없이 기존의 HTML 코드를 그대로 쓸 수 있다.

## 👎🏼 Tailwind CSS의 단점

### 1. 못생긴 코드

인라인태그로 작성하다 보니 코드가 조잡해 보여 익숙하지 않은 초반엔 가독성이 떨어지기 쉽다.

### 2. 초반 클래스명 러닝 커브

대부분의 클래스명이 기존 CSS 와 유사하나, 정확한 각 스타일의 클래스명을 익히기 위해 초반에는 문서를 참고해야한다. 하지만 계속 사용하다 보면 익숙해지고, 자동완성 익스텐션인 Tailwind CSS IntelliSense 를 사용하면 해결 가능하다.

### 3. HTML와 CSS 코드 혼재

장점이자 단점이 될 수 있는 부분.

HTML와 CSS의 관심사 분리가 이루어지지 않는다는 점에서 관점에 따라 단점이 될 수 있다.

---

### **`tailwind`** 제공 라이브러리

### 🤯 headlessUI

- react / vue 제공
- Dropdown / Select / Toggle / Modal / Transition / Tab 최근 Autocomplete 까지 추가.

Link to 👉🏼 [Headless UI](https://headlessui.dev/)

### 😋 HeroIcons

- react / vue 제공
- svg 아이콘 제공, tailwind 로 아이콘 커스터마이징 가능

```jsx
//basic
<svg
  class="h-6 w-6 text-gray-500"
  fill="none"
  viewBox="0 0 24 24"
  stroke="currentColor"
  stroke-width="2"
>
  <path
    stroke-linecap="round"
    stroke-linejoin="round"
    d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
  />
</svg>;

//react
import { BeakerIcon } from "@heroicons/react/solid";

function MyComponent() {
  return (
    <div>
      <BeakerIcon className="h-5 w-5 text-blue-500" />
      <p>...</p>
    </div>
  );
}
```

Link to 👉🏼 [Heroicons](https://heroicons.com/)
