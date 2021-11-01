# 정규표현식

- title : [신규 아이디 추천](https://github.com/dagchigo-ssgtudy/dagchigo-ssgtudy/blob/main/Algorithm/%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D/%EC%8B%A0%EA%B7%9C%20%EC%95%84%EC%9D%B4%EB%94%94%20%EC%B6%94%EC%B2%9C.html)
- keyword : 정규표현식
- template :  
```js
//숫자만 찾기
  let num = /[0-9]/g
//알파벳 소문자, 대문자 제외해서 찾기
  let noneAlp = /[^a-zA-z]/g
// google 이나 naver 찾기
  let search = /google | naver/g
// 특수문자 찾기 1) 여러개를 찾을경우 배열안에 넣는다.
  let search = /[-. ]/g
// 특수문자 찾기 2) 하나를 찾을경우 \ 를 앞에 사용한다.
  let search = /\./g
// 반복되는 문자 찾기
1) 점 0개나 여러개인 경우(1개 제외) *
  let search = /\.*/g
  2) 0이 1개이상 되는경우
  let search = /0+/g
  3) a가 2개이상 5개 이하가 되는 경우
  let search = /a{2,5}+/g
```

=======================================

