# Algorithm

## About


## Table of Contents
- DFS
- BFS
- [정규표현식](https://github.com/dagchigo-ssgtudy/dagchigo-ssgtudy/tree/main/Algorithm/%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D#%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D)
- [Array](https://github.com/dagchigo-ssgtudy/dagchigo-ssgtudy/tree/main/Algorithm/Array#array)

## How to update?
Step 1. Content select
  - Solution : HTML file
   ```html
<html>
  <head>
    <meta charset="UTF-8" />
    <title>[프로그래머스]파일명 정렬</title> <!-- (문제 이름) -->
    <!-- todo : https://programmers.co.kr/learn/courses/30/lessons/17686 (문제 링크)--> 
  </head>
  <body>
    <script>
      function solution(files) { // (풀이 시작, 풀이에 대한 설명은 주석으로 추가)

      } // (풀이 끝)

      // TEST CASE
      // ["img12.png", "img10.png", "img02.png", "img1.png", "IMG01.GIF", "img2.JPG"]
      let files = [
        "F-5 Freedom Fighter",
        "B-50 Superfortress",
        "A-10 Thunderbolt II",
        "F-14 Tomcat",
      ];

      console.log(solution(files)); // (콘솔에서 확인 가능하도록 작성)
    </script>
  </body>
</html>
```


Step 2. Algorithmic analysis
  - README.md file
  - title : [프로그래머스]파일명 정렬
  - keyword : 문제를 읽고 풀이 유형을 결정하게 된 키워드
  ```
  출력형식 => "정렬된 배열" 을 출력한다
  ```
  - template : (위 문제 기준 예) 
    1. 정렬 
    ```js
    sort((a, b) => a - b)
    ```
    2. 정규식 
    ```js
    // ^ : 시작부분부터, \D : 숫자가 아닌 것, + : 연속으로 반복되는 것
    match(/^\D+/)
    // /d : 숫자인 것, + : 연속으로 반복되는 것
    match(/\d+/)[0].replace(/^0+/, "")
    ```
    
