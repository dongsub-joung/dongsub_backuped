---
title: VanillaJS Challenge (5)
tag: VanillaJS Challenge
---



## 조건

1. Make a To Do list with two boards: **Pending**, **Finished.**
2. Allow the user to switch between boards.
3. Allow the user to delete To Dos.
4. Save everything on **localStorage** and restore everything **on refresh**.

수요일 AM 06:00 까지

---

## 알고리즘

> 시작 전 개요 

필요한 함수:

+ 박스 이벤트 `생성` 함수

+ 박스 이벤트의 자동 `submit`를 막는 함수

+ `localstorage`에 값을 저장하는 함수   *키 값이  `Pending`, `Finished`*
+ `value`의 키 값을 바꾸는 함수
+ `value`의 값을 삭제하는 함수



> 추론

+ 일단 `pending`을 완성 시킴

  입력 받은 값 저장

  저장한 값을 불러 들여서 h6으로 추가해서 만듬

+ `delet`버튼의 이벤트를 만듬

+  `move`버튼의 이벤트를 만듬

+ `temp`값을 이용해서 교환?



---

## 실행

리스트를 만들 대는 <ul>에 클래스를 만들어 `innerhtml`

`createElement`로 <li>하위 원소로 

```js
 function listSave(text){
    const li= document.createElement("li"); //태그를 만들고
    const delBtn= document.createElement("button");
    const moBtn= document.createElement("button");
    delBtn.innerText= "❌"; //value값을 넣음
    moBtn.innerText="🚩";
    const span= document.createElement("span");
    span.innerText= text;
    li.appendChild(span);
    li.appendChild(delBtn);
    li.appendChild(moBtn);
    pending.appendChild(li);
    localStorage.setItem(pending_LS, text);
 }
```

`li`의 원소를 생성, button이라는 원소 생성 그리고 `X`라는 텍스트를 삽입

`span`원소 생성 그리고 텍스트(=텍스트 변수)를 삽입

<li>에 `id`를 할당해야 어떤 버튼이 눌렸는지 안다. class로는 모른다는 말

배열을 저장하면 string이 아닌 obj으로 저장됨. `JSON` 필요



