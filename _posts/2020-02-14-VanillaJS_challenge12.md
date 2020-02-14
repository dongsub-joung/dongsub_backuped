---
title: Calculator (2)
tag: VanillaJS Challenge
---



## 기능

입력받은 숫자와 연산자를 변수로 나누어 3개의 변수를 생성한 뒤 숫자 변수 두개와 연산자 변수 한개를 통합해서 연산하는 방법

- [x] 사칙 연산
- [x] 연산자 중복 방지
- [x] 결과 값의 출력
- [x] 계산기 디자인
- [x] 루트, 로그
- [x] 제곱

> ver0.1과의 차이점

ver0.2는 결과창에 연산자가 출력되지 않음.

루트와 로그 기능 구현



---

## 디자인

> HTML table태그

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8"/>
        <link rel="stylesheet" href="index.css">
        <title>Calculator</title>
    </head>
    <body>
        <table style="padding: 3%; padding-top: 4%;">
            <tr>
                <td colspan="4">
                    <input type="text" style="width: 96%; height: 80px; font-size: 30px; text-align: right; padding-right: 10px;">
                </td>
            </tr>

            <tr>
                <td>
                    <input class="btn multi" type="button" value="log" >
                </td>
                <td>
                    <input class="btn multi" type="button" value="√" >
                </td>
                <td>
                    <input class="btn multi" type="button" value="^">
                </td>
                <td>
                    <input class="btn multi" type="button" value="Ⅽ" >
                </td>
            </tr>

            <tr>
                <td>
                    <input class="btn num" type="button" value="7" >
                </td>
                <td>
                    <input class="btn num" type="button" value="8" >
                </td>
                <td>
                    <input class="btn num" type="button" value="9">
                </td>
                <td>
                    <input class="btn multi" type="button" value="+">
                </td>
            </tr>
    
            <tr>
                <td>
                    <input class="btn num" type="button" value="4" >
                </td>
                <td>
                    <input class="btn num" type="button" value="5" >
                </td>
                <td>
                    <input class="btn num" type="button" value="6">
                </td>
                <td>
                    <input class="btn multi" type="button" value="-">
                </td>
            </tr>
    
            <tr>
                <td>
                    <input class="btn num" type="button" value="1">
                </td>
                <td>
                    <input class="btn num" type="button" value="2">
                </td>
                <td>
                    <input class="btn num" type="button" value="3">
                </td>
                <td>
                    <input class="btn multi" type="button" value="*">
                </td>
            </tr>
    
            <tr>
                <td colspan="2">
                    <input class="btn num" type="button" value="0" style="width: 100%;">
                </td>
                
                <td>
                    <input class="btn" type="button" value="=" style="background-color: antiquewhite; border-width: 8px; border-bottom-color: white;">
                </td>
                <td>
                    <input class="btn multi" type="button" value="/ ">
                </td>
            </tr>
    
        </table>

        <input class="memo" type="text">
        

    <script src="index.js"></script> 
    </body>
</html>

```



---

## 기능

> 버튼을 통제하는 방식

```js
numbers.forEach(function(number) {
  number.addEventListener("click", handleNumberClick);
});
operations.forEach(function(operation) {
  operation.addEventListener("click", handleOperationClick);
});
reset.addEventListener("click", handleReset);
equals.addEventListener("click", handleEqualsClick);
```

forEach를 활용해서 숫자면 숫자에 연산자면 연산자에 맞게 할당하고

```js
let firstValue = "",
  firstDone,
  secondValue = "",
  secondDone,
  currentOperation;
```

변수를 나누어 받음.

_결과적으로 출력에 연산자가 포함되지 않음_



