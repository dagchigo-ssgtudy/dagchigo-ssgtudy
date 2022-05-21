# Google IO 2022 keynote 정리

<p> 🌏 what's new web platform 주제 한정, <br/>
업데이트된 google에서 발표한 새로운 소식 정리 </p>

[Google I/O 2022](https://io.google/2022/intl/ko/)

## performance

### bfcache

- going back to forth, instantly
- 크롬부터 파이어폭스,사파리 엣지 전부 지원
- bfcache가 활성화되지 않은 경우 : 이전 페이지를 로드하기 위해 새 요청이 시작되고 해당 페이지가 반복 방문에 대해 얼마나 최적화되었는지에 따라 브라우저는 리소스의 일부(또는 전체)를 다시 다운로드하고, 다시 구문 분석하고, 다시 실행한다.
- bfcache가 활성화된 경우 :페이지 로드 성능 개선을 위해, 브라우저에서 페이지 이동 시 잠시 동안 캐시를 보유하고 있는 기능이 엣지와 크롬에도 추가되었습니다. 페이지가 이동하는 동안, 이전 페이지가 잠시 유지되면서 사용자들에게 좀더 빠른 로딩을 제공하는 기능입니다.
  bfcache는 탐색 속도를 높일 뿐만 아니라 리소스를 다시 다운로드할 필요가 없기 때문에 데이터 사용량도 줄일 수 있다.

Link to 👉🏼 [참조](https://web.dev/bfcache/)

## css 관련

### accent color

- Customizable theming for base UI form controls
- 기존에 변경이 불가능하던 input / radio button / checkbox / range slider / progress element 를 원하는 색으로 변경할 수 있다.
- 크롬부터 파이어폭스,사파리 엣지 전부 지원

```
.colorChange {
 accent-color:#232332;
//light 모드 , dark 모드
 color-scheme:light dark;
}
```

### dialog

- modals with accessibility and usability built-in
- 내장된 모달, 스타일 적용가능
- 2022 부터 사파리에도 적용.

```jsx
<dialog className='demo-dialog'>
  <form method='cancle'>
    <button value='cancle'>Cancle</button>
    <button value='confirm'>Confirm</button>
  </form>
</dialog>

<script>
  const dialog = document.querySelector('.demo-dialog')
  dialog.addEventListner('close',()=>{console.log(dialog.returnValue)'});
</script>
```

<img width="488" alt="스크린샷 2022-05-15 오후 5 06 44" src="https://user-images.githubusercontent.com/80618616/168477926-9dee19e1-9cad-4da0-93f3-fbb647f0c9bb.png">

### select menu

- 엣지, 크롬만 지원
- dropdown 메뉴 스타일 커스터마이징 지원

### datetime-local

- input type for multi-value entry of date and time content
- 모든 환경 지원

```jsx
<label>
  start date &amp; time:
  <input type="datetime-local" />
</label>
```

<img width="1384" alt="스크린샷 2022-05-15 오후 5 13 56" src="https://user-images.githubusercontent.com/80618616/168477972-61fc52cf-662b-4d78-b7ca-7e39864f8c3a.png">

### COLRv1

- new color gradient vector font with improved compositing and blending
- chrome, edge 만 지원
- WOFF2 Size in MB

<img width="595" alt="스크린샷 2022-05-15 오후 5 16 44" src="https://user-images.githubusercontent.com/80618616/168477968-7e59907d-44e8-43c1-a716-900f9ead5e1a.png">

### Image lazy loading

- img 태그에 기본적으로 제공되던 loading의 lazy 기능이 사파리에서도 사용 가능

```
<img src='...' alt='...' loading='lazy' />
<iframe src='...' loading='lazy'></iframe>
```

### Eyedropper API

- 사진에서 컬러를 추출할 수 있는 기능
- 크롬 , 엣지에서만 지원
  <img width="748" alt="스크린샷 2022-05-21 오후 1 07 09" src="https://user-images.githubusercontent.com/80618616/169634770-647402b0-69c5-4505-a396-04e1e034130e.png">

```js
const eyeDropper = new EyeDropper();
```

### aspect ratio

- maintain the relative dimensions of the element

```
.whatever {
  aspect-ratio: 16/9 ;
}
```

<img width="1008" alt="스크린샷 2022-05-21 오후 12 40 25" src="https://user-images.githubusercontent.com/80618616/169634052-309ab6fd-d98d-48a3-96d0-fc9aad0d6e41.png">

### Priority hint

- 이미지 또는 아이프레임의 노출 우선 순위를 결정하는 속성
- 여러 개의 이미지나 스크립트, 아이프레임 등을 불러올 때 상대적으로 중요하거나 먼저 보여주고 싶은 태그에 우선 순위를 부여하여 미리 로드되도록 할 수 있다.

```js
<img fetchpriority='high' src='important.webp' alt='...' />
<img fetchpriority='low' src='less-important.webp' alt='...' />

<script fetchpriority='high' src='important.js' async></script>
<script fetchpriority='low' src='less-important.js' async></script>

<iframe fetchpriority='high' src='/important'></iframe>
<iframe fetchpriority='low' src='/less-important'></iframe>

<script>
	fetch(url, { priority: 'low' });
</script>
```

<img width="1046" alt="스크린샷 2022-05-21 오후 12 44 25" src="https://user-images.githubusercontent.com/80618616/169634141-ef046d48-0c01-4254-b809-7de823e42bc0.png">

## privacy and security

### 🍪 chip

- 타사의 쿠키 및 사이트 간 추적을 단계적으로 중단하여 사용자 개인 정보를 개선
- 크롬에서만 제공중
  <img width="630" alt="스크린샷 2022-05-21 오후 12 56 20" src="https://user-images.githubusercontent.com/80618616/169634465-aa489311-f19c-4971-9ab5-cb59d09f3427.png">

<img width="752" alt="스크린샷 2022-05-21 오후 12 51 24" src="https://user-images.githubusercontent.com/80618616/169634327-5fb5e1cf-c846-4a8f-9702-2095b609e1df.png">

사이트 내부에 로그인 상태를 관리하는 채팅 앱이 내장되어 있다고 가정해 볼때,
사이트가 포함된 위치에 관계없이 고유한 단일 쿠키 세트를 갖도록 허용함으로써, 타사의 쿠키는 사라지게 됩니다. 이렇게 하면 개인 정보 보호에는 좋지만, 채팅에 자체 쿠키가 없으면 로그인 여부를 기억할 수 없어 매번 로그아웃이 되거나 다른 플랫폼 또는 사이트에서 도움을 받아야 할 경우 큰 문제가 될 수 있습니다.

<img width="1053" alt="스크린샷 2022-05-21 오후 12 55 46" src="https://user-images.githubusercontent.com/80618616/169634449-0bf1fe74-9de4-416b-93df-bff97377f33d.png">

칩을 가진 쿠키는 쿠키의 유용한 부분은 보존하고 사이트 간 추적 부분은 제거하여 현재 독립적인 파티션 상태.
쿠키에 Partitioned 속성을 넣으면, 쿠키는 차단되지 않으면서 공유되지 않는다.

<img width="952" alt="스크린샷 2022-05-21 오후 1 00 55" src="https://user-images.githubusercontent.com/80618616/169634607-614ad77e-61d9-4939-a8e3-91bafe93461c.png">

### 🔐 WebAuthn

- WebAuthn은 브라우저 및 사이트가 FIDO 표준에 기반한 외부 인증자 키를 사용할 수 있게 하는 웹 API를 정의

## Web app capabilities

### 🖥 Media Session API

- 웹에서도 앱과 같이 풍부한 플랫폼 경험이 가능한 API
- Media Session API를 사용하면 웹을 통해 이 모든 작업을 수행할 수 있다.
- Window, Mac OS, Android 및 iOS에서 미디어 컨트롤을 표시하고 이에 반응할 수 있다.

<img width="733" alt="스크린샷 2022-05-21 오후 1 05 09" src="https://user-images.githubusercontent.com/80618616/169634734-00cc5fbb-ef8f-4cce-9060-8644920f0c9a.png">

ex ) 휴대전화에서는 노래가 재생되지만 시계에서는 미디어 컨트롤이 표시

```js
navigator.mediaSession.metadata = new MediaMetadata({
  title: "Never Gonna Give You Up",
  artist: "Rick Astley",
  album: "Whenever You Need Somebody",
  artwork: [
    // ...
  ],
});
```

## javaScript

### array.at

- 모든 브라우저 제공
- 배열의 맨 마지막 값 구하는 메소드
- 배열 인덱스에서 항목을 가져온다.
- 음수 인덱스를 허용하기 때문에 끝에서부터 계산.

```js
// 기존
const last = array[array.length - 1];
const last = array.slice(-1)[0];

// array.at
const last = array.at(-1);
```

### Structured cloning

- 한줄로 깊은복사 가능
- 모든 브라우저 지원
- 객체뿐 아니라 이미지, 비트맵, 배열과 같은 더 많은 것들 깊은복사 가능
- 순환 참조가 있는 개체 구조도 복사할 수 있다.

```js
// 기존 객체의 깊은복사
const clone = JSON.Parse(
	JSON.stringify(obj);
);

// structuredClone 한줄로 가능
const clone = structuredClone(obj);
```
