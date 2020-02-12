---
title: Momentom clon
tag: VanillaJS Challenge
---



## 기능

- [x] 현재 시간
- [x] 현재 온도
- [x] 이름 
- [x] 할 일 리스트
- [x] 명언



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

   

+ Help 질문

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

일단 gg 백엔드 배우면 다시 온다.



---

## 이렇게 된 이상...

```js
const quotes={
    1: `Nothing is as far away as one minute ago (Jim Bishop)`,
    2: `Regret for wasted time is more wasted time. (Mason Cooley)`,
    3: `So little time and so little to do. (Oscar Levant)`,
    4:  ` Time is an illusion. Lunchtime doubly so. (Douglas Adams)`,
    5:  `Employ thy time well, if thou meanest to get leisure. (Benjamin Franklin) `,
    6:  ` Punctuality is the soul of business. (Thomas Halyburton) `,
    7: `The future ain't what it used to be. (Yogi Berra)`,
    8:  `Doing a thing well is often a waste of time. (Robert Byrne)`,
    9: `The future will be better tomorrow. (Dan Quayle)`,
    10: `Time is the most valuable thing a man can spend. (Theophrastus)`,
    11: `Time does not change us. It just unfolds us. (Max Frisch)`,
    12: `There is never enough time, unless you're serving it. (Malcolm Forbes)`,
    13: `You may delay, but time will not. (Benjamin Franklin)`,
    14: `If you judge people, you have no time to love them. (Mother Teresa)`,
    15: `We must use time as a tool, not as a crutch. (John F. Kennedy)`,
    16: `Early morning hath gold in its mouth. (Benjamin Franklin)`,
    17: `I have seen the future and it doesn't work. (Robert Fulford)`,
    18: `I may lose land...but I never lose a minute. (Napoleon Bonaparte)`,
    19: `An unhurried sense of time is in itself a form of wealth. (Bonnie Friedman)`,
    20: `People find life entirely too time-consuming. (Stanislaw J. Lec)`,
    21: `I wasted time, and now doth time waste me. (William Shakespeare)`,
    22:  `The empires of the future are the empires of the mind. (Sir Winston Churchill)`,
    23: `Fish and visitors smell in three days. (Benjamin Franklin)`,
    24: `Nothing is a waste of time if you use the experience wisely. (Auguste Rodin)`,
    25: `If time flies when you're having fun, it hits the afterburners when you don't think you're having enough. (Jef Mallett)`,
    26: `The time to repair the roof is when the sun is shining. (John F. Kennedy)`,
    27: `The future is much like the present, only longer. (Dan Quisenberry)`,
    28: `In the future everyone will be famous for 15 minutes. (Andy Warhol)`,
    29: `A single day is enough to make us a little larger. (Paul Klee)`,
    30: `The future depends on what we do in the present. (Mahatma Gandhi)`

};

const qut= document.querySelector(".quote");
const val= Math.random()*30; 
const num= Math.floor(val)+1;
qut.innerHTML= quotes[num];
```

아 코딩했다.....