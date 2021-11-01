# Array

- title : [정수 내림차순으로 배치하기](https://github.com/dagchigo-ssgtudy/dagchigo-ssgtudy/blob/main/Algorithm/Array/%EC%A0%95%EC%88%98%20%EB%82%B4%EB%A6%BC%EC%B0%A8%EC%88%9C%EC%9C%BC%EB%A1%9C%20%EB%B0%B0%EC%B9%98%ED%95%98%EA%B8%B0.html)
- keyword : 자료타입 핸들링
- template :  
```js
1. 정렬
 - arr.sort(a, b => { return b -a } : 내림차순 정렬
2. 문자 split("")
 - str.split("") : 문자열을 배열로 
3. 배열조인 join("")
 - arr.join(""): 배열을 문자열로
```


=======================================
- title : [자연수 뒤집어 배열로 만들기](https://github.com/dagchigo-ssgtudy/dagchigo-ssgtudy/blob/main/Algorithm/Array/%EC%9E%90%EC%97%B0%EC%88%98%20%EB%92%A4%EC%A7%91%EC%96%B4%20%EB%B0%B0%EC%97%B4%EB%A1%9C%20%EB%A7%8C%EB%93%A4%EA%B8%B0.html)
- keyword : 문자열, 숫자열
- template :  
```js
문자열을 숫자열로 바꾸는 방법:
1. +문자
2. 문자 * 1
3. Number(문자)
4. parseInt(문자)     // 정수
5. parseFloat(문자)   // 실수
```

=======================================
- title : [두 개 뽑아서 더하기](https://github.com/dagchigo-ssgtudy/dagchigo-ssgtudy/blob/main/Algorithm/Array/%EB%91%90%20%EA%B0%9C%20%EB%BD%91%EC%95%84%EC%84%9C%20%EB%8D%94%ED%95%98%EA%B8%B0.html)
- keyword : 중복제거하는 방법 : includes(), new Set(), filter(), indexOf()
- template : 
```js
여기다가 채워주세요
```
=======================================
- title : [로또위 최고순위와 최저순위](https://github.com/dagchigo-ssgtudy/dagchigo-ssgtudy/blob/main/Algorithm/Array/%EB%A1%9C%EB%98%90%EC%9D%98%20%EC%B5%9C%EA%B3%A0%EC%88%9C%EC%9C%84%EC%99%80%20%EC%B5%9C%EC%A0%80%EC%88%9C%EC%9C%84.html)
- keyword : `등수를 찾기 위해 lottos 배열과 win_nums 배열의 동일한 요소의 갯수를 찾아야 한다.` -> 배열 내 완전탐색
- template :
```js
1. Array.protytype.includes()
  // 배열의 특넝 요소를 포함하고 있는지 판별
 [1, 2, 3].includes(3) // true

2. Array.prototype.find()
  // 주어진 판별 함수를 만족하는 첫번째 요소의 값을 반환
  [1, 2, 3].find((element) => element > 1) // 2
  
3. Array.prototype.filter()
 // 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환
 [1, 2, 3].filter((element) => element > 1) // [2, 3]
 
4. Array.prototype.forEach()
 // 주어진 함수를 배열 요소 각각에 대해 실행
 [1, 2, 3].forEach((element) => element *= 2) // [2, 4, 6]
```
=======================================
