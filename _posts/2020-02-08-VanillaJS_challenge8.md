---
title: VanillaJS Challenge (8)
tag: VanillaJS Challenge
---



## 조건

**The final project should have the following features:**

1. Clock.
2. Username Persistance.
3. To Do List.
4. Random Background Image.
5. Weather with Geolocation.

> This is a two day challenge.
>
> Based on the section #3
>
> **Finish** the course project and **deploy** to Github Pages.



---

## 알고리즘

1. clock

현재 시간을 가져오기

시간을 갱신 1000ms

시간 출력

2. Username Persistance.

유저 이름을 입력 받음

유저이름을 저장	/	 불러옴

유저이름 입력창을 숨기고 거기에 text출력





---

## 1. Clock

```js
let div= document.querySelector(`.div`);
let clock= document.querySelector(".clock");

let clockSec= document.querySelector("#clockSec");
function getDate(){
    let toDay= new Date();
    let hours= toDay.getHours(),
     min= toDay.getMinutes(),
     sec= toDay.getSeconds();
    clock.innerHTML= `
        ${hours < 10 ? `0${hours}` : hours}
        : ${min < 10 ? `0${min}` : min}
    `
    clockSec.innerHTML = `:${sec < 10 ? `0${sec}` : sec}`
}

setInterval(getDate, 1000);
```

_시계를 한 클래스로 묶고 innerHTML하니까 sec에 해당하는 부분이 CSS 태그가 안먹혀서 span을 이용해서 분리 후 적용 시킴_





