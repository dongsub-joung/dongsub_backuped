---
title: VanillaJS Challenge (3)
tag: VanillaJS Challenge
---



## 조건

+ Using the boilerplate, make an app that shows the **time until Christmas Eve** in days, hours, minutes and seconds.

- [Date() documentation](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date)﻿.
- Keep in mind: new Date() might not in KST (Korean Time), if then you have to fix that.
- **(fix) 2020년 기준으로 진행해주시면 됩니다!**



---

## 알고리즘

1. 현재 시간 구하기
2. 2020년 크리스마스 이브 00시 구하기
3.  2)에서 1)를 빼기 
4. 뺀 값에서 1초를 뺌(그리고 1초마다 갱신)
5. 뺀 값이 0보다 작으면 함수를 삭제



---

## 실행

[Javascript 타이머 만들기](https://basketdeveloper.tistory.com/4)

+ 현재와  크리스마스 이브 시간 가져오기 

> [getTime]([https://webisfree.com/2017-04-07/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%82%A0%EC%A7%9C%EC%97%90%EC%84%9C-gettime()%EC%9C%BC%EB%A1%9C-%EC%96%BB%EC%96%B4%EC%98%A8-%EA%B0%92%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94](https://webisfree.com/2017-04-07/자바스크립트-날짜에서-gettime()으로-얻어온-값은-무엇인가요)

1970년 1월 1일 자정을 기준

현재시간을 숫자로 나열한 것

나열된 시간은 millisecond. 1/1000초

+ `millisecond`를 `day`, `hours`, `min`, `sec`로 변환










