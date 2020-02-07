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