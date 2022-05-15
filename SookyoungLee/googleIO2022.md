# Google IO 2022 keynote 정리

<p> 🌏 what's new web platform 주제 한정, <br/>
업데이트된 google에서 발표한 새로운 소식 정리 </p>

[Google I/O 2022](https://io.google/2022/intl/ko/)

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

## java script 관련

업뎃예정 ,, , ,,🐰 ,,
