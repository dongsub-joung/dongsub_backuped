---
title: VanillaJS Challenge (7)
tag: VanillaJS Challenge
---



## 조건

**JS Calculator!**

>  This is a two day challenge.
>
> Based on the section #3
>
> Make a calculator using only Vanilla JS!



**The calculator should:**

1. Have a **reset** (C) button.
2. Support **all** basic operations (+ , - , * , / )
3. Support for **'equals' ( = )** button.
4. Allow value carrying. i.e 2 * 2 * 2 * 2 * 2 **without** pressing equals.
5. Don't give up!



---

## 알고리즘

> 필요한 기능

1. 리셋 버튼과 기능

   저장된 값 삭제

   입력된 값 삭제

2. 사칙연산 버튼과 기능

   +,-,*,/ 버튼 생성

   사칙 연산 함수의 배열 생성

3. 합 버튼(=)과 기능

   입력된 변수를 함수에 대입해서 결과값을 리턴

4. 계산된 값을 저장하는 기능

5. 제곱 연산의 경우 계산값이 리얼타임으로 표시

   제곱 연산의 함수? 매소드를 사용해서 값을 리턴

   

---

## 실행1

### HTML

1. 버튼 만들고 지정하기.

`button-value`로 버튼의 종류를 묶을려고 했는데 불가능. 

+ `class` 선언

  숫자는 `num`

  사칙연산은 `muti`

  리셋은 `clear`

  =은 `result`

  결과의 출력은 `viewer`

+ [데이터 속성 사용하기]([https://developer.mozilla.org/ko/docs/Learn/HTML/Howto/%EB%8D%B0%EC%9D%B4%ED%84%B0_%EC%86%8D%EC%84%B1_%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0](https://developer.mozilla.org/ko/docs/Learn/HTML/Howto/데이터_속성_사용하기))

  `data-multi`="plus", "minus", "times", "divided by"

  `data-result` 

  `data-num` = 0~9

> why?

_나는 특정 숫자에 id를 지정하고 그 id값을 대입하면 계산기를 만들 수 있을 것이라 생각했지만 더 간단한 방법은 이렇게 데이터 속성을 사용해서 숫자 데이터 값을 받은 다음 출력하면 되기때문에 이 방법이 필요_

_사칙 연산의 함수를 만들어서 배열을 만든 후 데이터 값에 이러한 함수를 넣으면 기능을 수행하지 않을까?_



+ `id` 선언

  버튼 C, =

   

### JS

> 입력된 / 숫자들을 /  사칙 / 연산해서  / 결과 값을 보여줌

+ 어떻게 입력되나?

버튼에 할당된 숫자들을 눌러서 

할당된 숫자들을 불러와서 사칙 연산의 함수에 넣을 필요성이 있음	 

num class를 누르면 data-num을 반환

muti class를 누르면 data-multi를 반환

id equals를 누르면 data-result를 반환

_다만 그 값이 ""이기 때문에 multi의 리턴값을 변환할 필요가 있음_

> _[JS calculator](https://codepen.io/giana/pen/GJMBEv) 이 과정이 너무 어렵게 돼있어 포기_
>
> +_내가 배운것과 너무 상이함_



---

## 실행 2

> `onclick`의 이용

```html
<input id="calculator">
<input id="viewer">


<stript>
	function add(){
    	calculator.value= calculator.value + char;
	}
</stript>
```

이렇게하고 CSS이용해서 calculator는 숨기고 계산 값만 viewer를 통해서 출력하면 간단히 가능하다. 하지만 조건은 only Javascript라고 하였다. 



---

## 실행 3

`실행 2`1는 add함수에 문자열까지 다 표기가 되었고 `eval`이라는 내장 함수도 사용했다. 

문제는 

1. _viewer에 string이 보여진다는 것_
2. _`eval`의 오류_

`eval`의 오류는 연속된 string이 있다면 연산오류가 나버리는 것.

이것을 해결하기 위해서는 string의 입력이 2번 초과일 경우 그 연산자에 대해서는 `calculator.value`에 추가하지 않아야한다.

```js
// 중간과정
// 구현해야할 것: 함수에 들어오는 변수가 숫자인지 연산자인지 구별해야함.
let tOf= false; // 2번 연속 연산자면 1, 아니면 0
function add(num){
    if(tOf === false){
        if( overlap(num) === true){

        } else {
            calculator.value += num;
            calculator.value= eval(calculator.value);
        }
    }else{
        calculator.value += num;
        calculator.value= eval(calculator.value);
    }
}
const multi= document.querySelector(".multi");
console.log(multi);

function overlap(num){
    if(num == String){
        tOf= true;
    } else{ 
        tOf= false;
    }
} 
```



### `eval`의 오류: 연속된 string이 있다면 연산오류가 나버리는 것의 해결

> [HTML + javascript 계산기 만들기 프로젝트!](https://blog.cordelia273.space/32)

```js
var numberClicked = false; // 전역 변수로 numberClicked를 설정
    function add (char) {
        if(numberClicked == false) { // 만약 이전에 연산자를 입력 했는데,
            if(isNaN(char) == true) { // 입력 받은 값이 또 다시 연산자면,
                // 아무것도 하지 않는다.
            } else { // 연산자가 아니라면!
                document.getElementById('display').value += char; // 식 뒤에 값을 추가한다.
            }
        } else { // 만약에 이전에 숫자를 입력 했으면,
            document.getElementById('display').value += char; // 식 뒤에 값을 추가한다.
        }
 
 
        // 다음 입력을 위해 이번 입력에 숫자가 눌렸는지 연산자가 눌렸는지 설정한다.
        if(isNaN(char) == true) { // "만약 숫자가 아닌게 참이라면" = "연산자를 눌렀다면"
            numberClicked = false; // numberClicked를 false로 설정한다.
        } else {
            numberClicked = true; // numberClicked를 true로 설정한다.
        }
    }
```

> [javascript 계산기 / 자바스크립트 계산기 만들기](https://cofs.tistory.com/209)

```js
   if (isNaN(su))  
    {
        flag2++;
    }else{
        flag2 = 0;
        }
        
    if (flag2 >1)  
    {
        return; //43# : 문자 입력이 2번 이상이면 리턴
    }
    f.disp.value += su;   
}
```

_inNaN function으로 숫자인지 문자열인지 판단_

_count 변수를 만들어서 연산자가 입력된 수를 제어_

> 완성

```js
function add(num){
//input이 숫자인지 문자인지 판별
    if(isNaN(num) == true){
        tofCount++;     //2연속 연산자면 0으로
    } else{ 
        tofCount=0;
    }

    if(tofCount > 1){
        return tof=true;
    } 

    if(tOf == false){
        claculation(num);
        calculator.value= eval(calculator.value);
    } else {    //2연속 연산자면
        return;
    }
}
```



---

### viewer에 string이 보여진다는 것의 해결

예시에서 곱셈일 경우 

2(2) , *(2) ,2(4), *(4), 2(8) 이런식으로 작동함



> [HTMLJavaScript-계산기-만들기](https://olsh1108o.tistory.com/entry/HTMLJavaScript-계산기-만들기)

내가 만든 계산기로는 이러한 것이 불가능함을 이것을 보고 깨달음. 코드를 갈아야함

어칼까 일단 내고 다시 만들자

