---
title: Momentom clon
tag: VanillaJS Challenge
---



## 기능

+ 현재 시간
+ 현재 온도
+ 이름 
+ 할 일 리스트
+ 명언



---



## 명언 기능 추가

+ [API](https://quotes.rest/#!/qod/get_qod) 얻기

fetch 해서 그 값을 받아서 출력하려고 함.

### 오류의 연속

```js
const say= document.querySelector(".quotes");

fetch(`http://quotes.rest/qod.js?category=inspire`)
 .then(function(response) {
     return response.json();	//여기서 오류남. json을 인식 못함.
})
 .then(function(myJson) {
    const val= JSON.stringify(myJson);	
	const quotes= val.contens.quotes;
    const auther= val.contens.auther;
    say.innerHTML= `${quotes} by ${auther}`;
});
```

> 자꾸 값을 찾을 수 없다.
>
> JSON이 정의되지 않았다. 
>
> null값이다.

   

+ fetch MDN을 참조

```js
const say= document.querySelector(".quotes");

fetch(`http://quotes.rest/qod.js?category=inspire`)
 .then(function(response) {
     return response.json();	//여기서 오류남. json을 인식 못함.
})
 .then(function(myJson) {
    console.log(JSON.stringify(myJson));	
});
```

>  Uncaught (in promise) SyntaxError: Unexpected token p in JSON at position 0 Promise.then (async) (anonymous) @ quotes.js:8

   

+ [Help](https://stackoverflow.com/questions/60176478/syntaxerror-unexpected-token-p-in-json-at-position-0-in-fetch?noredirect=1#comment106436190_60176478) 질문

1. 

try to add a content-type and accept to the headers

```js
const say= document.querySelector(".quotes");

fetch(`http://quotes.rest/qod.js?category=inspire`, {
  headers: {
    "Accept": "application/json",
    "Content-Type": "application/json"
  }
})
 .then(function(response) {
     return response.json();
})
 .then(function(myJson) {
    console.log(JSON.stringify(myJson));
});
```

>  error

Access to fetch at 'http://quotes.rest/qod.js?category=inspire' from origin 'null' has been blocked by CORS policy: Request header field content-type is not allowed by Access-Control-Allow-Headers in preflight response.

quotes.js:4 GET http://quotes.rest/qod.js?category=inspire net::ERR_FAILED

index.html:1 Uncaught (in promise) TypeError: Failed to fetch
Promise.then (async)
(anonymous) @ quotes.js:13

   

2. 

This endpoint is not returning application/JSON, it is returning application/javascript. This looks like its probably used as a part of a JSONP request because it is returning javascript that when executed continues the call chain.

> 문제 :
>
> endpoint not returning
>
> 해결:
>
> a JSONP request 

In order to interact with the endpoint you need to either have a library that supports JSONP such as jquery or implement the support yourself. https://en.wikipedia.org/wiki/JSONP

> have a library 
>
> JSONP 

   

_아아악 지금 명언 하나 받아서 출력하고 싶어서 이 난리를 피우다니이이이_

> http://quotes.rest/#!/qod/get_qod_categories
>
> 설명 제대로 읽어보자 



---

### [curl 설치](https://www.lesstif.com/pages/viewpage.action?pageId=14745703)

```
curl -X GET --header 'Accept: application/json' 'http://quotes.rest/qod?category=inspire'
```

이 조건을 충족시켜야 하는데 이건  

백 엔드 영역인데....



