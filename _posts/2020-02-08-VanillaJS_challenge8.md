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

2. Username Persistance

유저 이름을 입력 받음

유저이름을 저장	/	 불러옴

유저이름 입력창을 숨기고 거기에 text출력

3. To Do List

할일은 배열. 배열 선언

배열 입력 받기

> 2와 동일

배열 출력하기

> JSON을 이용







---

## 1. Clock

```js
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

   

---

## 2. Username Persistance

> 입력받은 값을 텍스트로 출력

+ 입력 값을 출력하는 함수

_새로운 js파일로 작업하면 꼭 꼭 script 추가하자_

```js
function paint(currentVal){
    form.classList.remove("form");
    userInput.classList.add(userName_CN);   
    userInput.innerHTML= `${input.value} ㅎㅇ`;
}
```

3번째 줄에 클래스를 추가하는 것은 값이 없어도 화면을 할당받기 때문에 

숨기고, 보여지는 것을 번갈아가면서 하기 위함 

   

+ 값을 입력 받는 이벤트

```js
function handleSubmit(event){
    event.preventDefault();
    const currentVal =input.value;
    paint(currentVal);
}
```



+ 유저이름을 저장	/	 불러옴

```js
function saveVal(currentVal){
    localStorage.setItem(`User`, currentVal);
}
```

+ 만약 저장된 키가 없다면

road가 시작점 if의



```js
//paint
const nameForm= document.querySelector(".nameForm"),
 input= document.querySelector("input"), 
 nameViewer= document.querySelector(".nameViewer");

const userName_CN="showing";

function paint(text){   //키값이 입력된 후/  키값이 있는지 확인하고 있으면 기존 값을 불러와서 출력
    nameForm.classList.remove(userName_CN);
    nameViewer.classList.add(userName_CN);   
    nameViewer.innerHTML= `Hi ${text}`;
}

function handleSubmit(event){   //입력값이 입력된 후 실행됨. 값을 저장하고, 출력함 이건 기존 값이 없어야 실행됨
    event.preventDefault();
    const currentVal = input.value;
    paint(currentVal);
    saveVal(currentVal);
}

function saveVal(currentVal){   //입력된 값을 저장
    localStorage.setItem(`User`, currentVal);
}

function load(){  //이함수가 필요할 때는 기존 값이 존재할 때. 그리고 존재하면 기존 값을 불러와서 페인트 아니면 입력값을 받아야함
    let currentVal= localStorage.getItem("User");
    if(currentVal !== null){    //기존 값이 존재하면
        paint(currentVal);
    } else {
        askName();
    }
}

function askName(){ //입력밧을 받기 위해서 창을 띄움 이것은 기존 값이 없어야 가능
    nameForm.classList.add(userName_CN);
    nameForm.addEventListener("submit", handleSubmit);
}

function init(){
    load();
}

init();
```





