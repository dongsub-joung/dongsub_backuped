---
title: youtube clone 
tag: nodejs
---

+ package.json 
  `scripts`

+ .gitignore
  모듈관리

+ express
  `라우터` 사용, 서버 열기

Q.  변수가 없으면 서버는 무한 Lording

> 서버는 일반적으로 HTTML을 응답하도록 함.

- request obj : 어떤 데이터가 전송되었는지
-  response obj

---

+ 루트 / : 

```
app.get("/profile", handleProfile);
​```

+ babel
  `stage`
  `preset` 

// 문법 변환 룰?

+ babelrc
  `preset` 저장, 컨트롤

+ 프로젝트의 `dependency`와 별개로 설치할 필요가 있을 때
  npm 라이브러리 끝에 `-D`
  
+ `nodemon`
  nodemon --exec // scripts

+ middleware
  유저와 마지막 응답사이에 존재하는 것.
  app.use //절차 지향

  > morgan, helmet, bodyparser, cookieParser

+ `router`를 이용해서 url 분할
  express.Router()
  export // import { userRouter } 
  `use`로 받으면 다음 라우터로 유저를 받음을 의미

---

+ Model, View, Control
  data, how does the data look, function that looks for the data
+ `Pub`
  express에서 View를 다루는 방식 중 하나 //HTML 전달 