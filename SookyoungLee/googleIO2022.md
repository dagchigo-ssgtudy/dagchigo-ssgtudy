# Google IO 2022 keynote μ λ¦¬

<p> π what's new web platform μ£Όμ  νμ , <br/>
μλ°μ΄νΈλ googleμμ λ°νν μλ‘μ΄ μμ μ λ¦¬ </p>

[Google I/O 2022](https://io.google/2022/intl/ko/)

## performance

### bfcache

- going back to forth, instantly
- ν¬λ‘¬λΆν° νμ΄μ΄ν­μ€,μ¬νλ¦¬ μ£μ§ μ λΆ μ§μ
- bfcacheκ° νμ±νλμ§ μμ κ²½μ° : μ΄μ  νμ΄μ§λ₯Ό λ‘λνκΈ° μν΄ μ μμ²­μ΄ μμλκ³  ν΄λΉ νμ΄μ§κ° λ°λ³΅ λ°©λ¬Έμ λν΄ μΌλ§λ μ΅μ νλμλμ§μ λ°λΌ λΈλΌμ°μ λ λ¦¬μμ€μ μΌλΆ(λλ μ μ²΄)λ₯Ό λ€μ λ€μ΄λ‘λνκ³ , λ€μ κ΅¬λ¬Έ λΆμνκ³ , λ€μ μ€ννλ€.
- bfcacheκ° νμ±νλ κ²½μ° :νμ΄μ§ λ‘λ μ±λ₯ κ°μ μ μν΄, λΈλΌμ°μ μμ νμ΄μ§ μ΄λ μ μ μ λμ μΊμλ₯Ό λ³΄μ νκ³  μλ κΈ°λ₯μ΄ μ£μ§μ ν¬λ‘¬μλ μΆκ°λμμ΅λλ€. νμ΄μ§κ° μ΄λνλ λμ, μ΄μ  νμ΄μ§κ° μ μ μ μ§λλ©΄μ μ¬μ©μλ€μκ² μ’λ λΉ λ₯Έ λ‘λ©μ μ κ³΅νλ κΈ°λ₯μλλ€.
  bfcacheλ νμ μλλ₯Ό λμΌ λΏλ§ μλλΌ λ¦¬μμ€λ₯Ό λ€μ λ€μ΄λ‘λν  νμκ° μκΈ° λλ¬Έμ λ°μ΄ν° μ¬μ©λλ μ€μΌ μ μλ€.

Link to ππΌ [μ°Έμ‘°](https://web.dev/bfcache/)

## css κ΄λ ¨

### accent color

- Customizable theming for base UI form controls
- κΈ°μ‘΄μ λ³κ²½μ΄ λΆκ°λ₯νλ input / radio button / checkbox / range slider / progress element λ₯Ό μνλ μμΌλ‘ λ³κ²½ν  μ μλ€.
- ν¬λ‘¬λΆν° νμ΄μ΄ν­μ€,μ¬νλ¦¬ μ£μ§ μ λΆ μ§μ

```
.colorChange {
 accent-color:#232332;
//light λͺ¨λ , dark λͺ¨λ
 color-scheme:light dark;
}
```

### dialog

- modals with accessibility and usability built-in
- λ΄μ₯λ λͺ¨λ¬, μ€νμΌ μ μ©κ°λ₯
- 2022 λΆν° μ¬νλ¦¬μλ μ μ©.

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

<img width="488" alt="αα³αα³αα΅α«αα£αΊ 2022-05-15 αα©αα? 5 06 44" src="https://user-images.githubusercontent.com/80618616/168477926-9dee19e1-9cad-4da0-93f3-fbb647f0c9bb.png">

### select menu

- μ£μ§, ν¬λ‘¬λ§ μ§μ
- dropdown λ©λ΄ μ€νμΌ μ»€μ€ν°λ§μ΄μ§ μ§μ

### datetime-local

- input type for multi-value entry of date and time content
- λͺ¨λ  νκ²½ μ§μ

```jsx
<label>
  start date &amp; time:
  <input type="datetime-local" />
</label>
```

<img width="1384" alt="αα³αα³αα΅α«αα£αΊ 2022-05-15 αα©αα? 5 13 56" src="https://user-images.githubusercontent.com/80618616/168477972-61fc52cf-662b-4d78-b7ca-7e39864f8c3a.png">

### COLRv1

- new color gradient vector font with improved compositing and blending
- chrome, edge λ§ μ§μ
- WOFF2 Size in MB

<img width="595" alt="αα³αα³αα΅α«αα£αΊ 2022-05-15 αα©αα? 5 16 44" src="https://user-images.githubusercontent.com/80618616/168477968-7e59907d-44e8-43c1-a716-900f9ead5e1a.png">

### Image lazy loading

- img νκ·Έμ κΈ°λ³Έμ μΌλ‘ μ κ³΅λλ loadingμ lazy κΈ°λ₯μ΄ μ¬νλ¦¬μμλ μ¬μ© κ°λ₯

```
<img src='...' alt='...' loading='lazy' />
<iframe src='...' loading='lazy'></iframe>
```

### Eyedropper API

- μ¬μ§μμ μ»¬λ¬λ₯Ό μΆμΆν  μ μλ κΈ°λ₯
- ν¬λ‘¬ , μ£μ§μμλ§ μ§μ
  <img width="748" alt="αα³αα³αα΅α«αα£αΊ 2022-05-21 αα©αα? 1 07 09" src="https://user-images.githubusercontent.com/80618616/169634770-647402b0-69c5-4505-a396-04e1e034130e.png">

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

<img width="1008" alt="αα³αα³αα΅α«αα£αΊ 2022-05-21 αα©αα? 12 40 25" src="https://user-images.githubusercontent.com/80618616/169634052-309ab6fd-d98d-48a3-96d0-fc9aad0d6e41.png">

### Priority hint

- μ΄λ―Έμ§ λλ μμ΄νλ μμ λΈμΆ μ°μ  μμλ₯Ό κ²°μ νλ μμ±
- μ¬λ¬ κ°μ μ΄λ―Έμ§λ μ€ν¬λ¦½νΈ, μμ΄νλ μ λ±μ λΆλ¬μ¬ λ μλμ μΌλ‘ μ€μνκ±°λ λ¨Όμ  λ³΄μ¬μ£Όκ³  μΆμ νκ·Έμ μ°μ  μμλ₯Ό λΆμ¬νμ¬ λ―Έλ¦¬ λ‘λλλλ‘ ν  μ μλ€.

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

<img width="1046" alt="αα³αα³αα΅α«αα£αΊ 2022-05-21 αα©αα? 12 44 25" src="https://user-images.githubusercontent.com/80618616/169634141-ef046d48-0c01-4254-b809-7de823e42bc0.png">

## privacy and security

### πͺ chip

- νμ¬μ μΏ ν€ λ° μ¬μ΄νΈ κ° μΆμ μ λ¨κ³μ μΌλ‘ μ€λ¨νμ¬ μ¬μ©μ κ°μΈ μ λ³΄λ₯Ό κ°μ 
- ν¬λ‘¬μμλ§ μ κ³΅μ€
  <img width="630" alt="αα³αα³αα΅α«αα£αΊ 2022-05-21 αα©αα? 12 56 20" src="https://user-images.githubusercontent.com/80618616/169634465-aa489311-f19c-4971-9ab5-cb59d09f3427.png">

<img width="752" alt="αα³αα³αα΅α«αα£αΊ 2022-05-21 αα©αα? 12 51 24" src="https://user-images.githubusercontent.com/80618616/169634327-5fb5e1cf-c846-4a8f-9702-2095b609e1df.png">

μ¬μ΄νΈ λ΄λΆμ λ‘κ·ΈμΈ μνλ₯Ό κ΄λ¦¬νλ μ±ν μ±μ΄ λ΄μ₯λμ΄ μλ€κ³  κ°μ ν΄ λ³Όλ,
μ¬μ΄νΈκ° ν¬ν¨λ μμΉμ κ΄κ³μμ΄ κ³ μ ν λ¨μΌ μΏ ν€ μΈνΈλ₯Ό κ°λλ‘ νμ©ν¨μΌλ‘μ¨, νμ¬μ μΏ ν€λ μ¬λΌμ§κ² λ©λλ€. μ΄λ κ² νλ©΄ κ°μΈ μ λ³΄ λ³΄νΈμλ μ’μ§λ§, μ±νμ μμ²΄ μΏ ν€κ° μμΌλ©΄ λ‘κ·ΈμΈ μ¬λΆλ₯Ό κΈ°μ΅ν  μ μμ΄ λ§€λ² λ‘κ·Έμμμ΄ λκ±°λ λ€λ₯Έ νλ«νΌ λλ μ¬μ΄νΈμμ λμμ λ°μμΌ ν  κ²½μ° ν° λ¬Έμ κ° λ  μ μμ΅λλ€.

<img width="1053" alt="αα³αα³αα΅α«αα£αΊ 2022-05-21 αα©αα? 12 55 46" src="https://user-images.githubusercontent.com/80618616/169634449-0bf1fe74-9de4-416b-93df-bff97377f33d.png">

μΉ©μ κ°μ§ μΏ ν€λ μΏ ν€μ μ μ©ν λΆλΆμ λ³΄μ‘΄νκ³  μ¬μ΄νΈ κ° μΆμ  λΆλΆμ μ κ±°νμ¬ νμ¬ λλ¦½μ μΈ νν°μ μν.
μΏ ν€μ Partitioned μμ±μ λ£μΌλ©΄, μΏ ν€λ μ°¨λ¨λμ§ μμΌλ©΄μ κ³΅μ λμ§ μλλ€.

<img width="952" alt="αα³αα³αα΅α«αα£αΊ 2022-05-21 αα©αα? 1 00 55" src="https://user-images.githubusercontent.com/80618616/169634607-614ad77e-61d9-4939-a8e3-91bafe93461c.png">

### π WebAuthn

- WebAuthnμ λΈλΌμ°μ  λ° μ¬μ΄νΈκ° FIDO νμ€μ κΈ°λ°ν μΈλΆ μΈμ¦μ ν€λ₯Ό μ¬μ©ν  μ μκ² νλ μΉ APIλ₯Ό μ μ

## Web app capabilities

### π₯ Media Session API

- μΉμμλ μ±κ³Ό κ°μ΄ νλΆν νλ«νΌ κ²½νμ΄ κ°λ₯ν API
- Media Session APIλ₯Ό μ¬μ©νλ©΄ μΉμ ν΅ν΄ μ΄ λͺ¨λ  μμμ μνν  μ μλ€.
- Window, Mac OS, Android λ° iOSμμ λ―Έλμ΄ μ»¨νΈλ‘€μ νμνκ³  μ΄μ λ°μν  μ μλ€.

<img width="733" alt="αα³αα³αα΅α«αα£αΊ 2022-05-21 αα©αα? 1 05 09" src="https://user-images.githubusercontent.com/80618616/169634734-00cc5fbb-ef8f-4cce-9060-8644920f0c9a.png">

ex ) ν΄λμ νμμλ λΈλκ° μ¬μλμ§λ§ μκ³μμλ λ―Έλμ΄ μ»¨νΈλ‘€μ΄ νμ

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

- λͺ¨λ  λΈλΌμ°μ  μ κ³΅
- λ°°μ΄μ λ§¨ λ§μ§λ§ κ° κ΅¬νλ λ©μλ
- λ°°μ΄ μΈλ±μ€μμ ν­λͺ©μ κ°μ Έμ¨λ€.
- μμ μΈλ±μ€λ₯Ό νμ©νκΈ° λλ¬Έμ λμμλΆν° κ³μ°.

```js
// κΈ°μ‘΄
const last = array[array.length - 1];
const last = array.slice(-1)[0];

// array.at
const last = array.at(-1);
```

### Structured cloning

- νμ€λ‘ κΉμλ³΅μ¬ κ°λ₯
- λͺ¨λ  λΈλΌμ°μ  μ§μ
- κ°μ²΄λΏ μλλΌ μ΄λ―Έμ§, λΉνΈλ§΅, λ°°μ΄κ³Ό κ°μ λ λ§μ κ²λ€ κΉμλ³΅μ¬ κ°λ₯
- μν μ°Έμ‘°κ° μλ κ°μ²΄ κ΅¬μ‘°λ λ³΅μ¬ν  μ μλ€.

```js
// κΈ°μ‘΄ κ°μ²΄μ κΉμλ³΅μ¬
const clone = JSON.Parse(
	JSON.stringify(obj);
);

// structuredClone νμ€λ‘ κ°λ₯
const clone = structuredClone(obj);
```
