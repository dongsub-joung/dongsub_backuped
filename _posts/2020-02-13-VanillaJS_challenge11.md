---
title: Calculator (1)
tag: VanillaJS Challenge
---



## 기능

1. 입력받은 숫자와 연산자를 통채로 연산하는 방법

- [x] 사칙 연산
- [x] 연산자 중복 방지
- [x] 결과 값의 출력
- [x] 계산기 디자인

> HTML의 onclick 이용

---

## 디자인

> 모델

![993E1E355B06A81B13](https://user-images.githubusercontent.com/59364300/74423741-17399f00-4e94-11ea-8c3a-c879e96c9e94.png)

padding, margin 0으로 하고 

boder 1px

0만 좀 길게하고 

사칙연산 배경색 넣고

결과창 margin-left 좀 넣어서 공간 만들고 배경색

> 버튼 배열은

결과창 | c

7 8 9 +

4 5 6 -

1 2 3 *

0  = /

   

---

## 계산기 1

### HTML

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8"/>
        <link rel="stylesheet" href="index.css"/>
        <title>Calculator</title>
    </head>
    <body>
        
     <div>
        <input id="calculator">
        <button class="reset" onclick="reset()">C</button> <br>
        
        <button value="7" onclick="add(7)">7</button>
        <button value="8" onclick="add(8)">8</button>
        <button value="9" onclick="add(9)">9</button>
        <button class="multi" onclick="add(`+`)">+</button> <br>

        <button value="4" onclick="add(4)">4</button>
        <button value="5" onclick="add(5)">5</button>
        <button value="6" onclick="add(6)">6</button>
        <button class="multi" onclick="add(`-`)">-</button> <br>

        <button value="1" onclick="add(1)">1</button>
        <button value="2" onclick="add(2)">2</button>
        <button value="3" onclick="add(3)">3</button>
        <button class="multi" id="multi" onclick="add(`*`)">*</button> <br>

        <button class="zero" value="0" onclick="add(0)">0</button>
        <button  id="equals" onclick="result()">=</button>
        <button class="multi" onclick="add(`/`)">/</button> <br>
     </div>  
    
    <script src="index.js"></script> 
    </body>
</html>

```

   

### JS

```js
const calculator= document.getElementById("calculator"),
 equals= document.getElementById("equals");

let tOf= false, // 2번 연속 연산자면 1, 아니면 0
 tofCount=0;

function add(num){  //input이 숫자인지 문자인지 판별
    if(isNaN(num) == true){
        tofCount++;     //2연속 연산자면 0으로
    } else{ 
        tofCount=0;
    }

    if(tofCount > 1){
        return tOf=true;
    } 

    if(tOf == false){
        claculation(num);
    } else { 
        return;
    }
}

function claculation(num){
    if(isNaN(num) === 1){
        return;
    } else{
        calculator.value += num;
    }
}


function result(){
    calculator.value= eval(calculator.value);
}

function reset(){
    calculator.value="";
}
```



