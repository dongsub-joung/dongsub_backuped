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

## 실행

1. html에서 버튼 만들고 id지정하기.

`button-value`로 버튼의 종류를 묶을려고 했는데 불가능. 

+ `class` 선언

  숫자는 `num`

  사칙연산은 `muti`

  리셋은 `clear`

  결과값은 `viewer`

+ [데이터 속성 사용하기]([https://developer.mozilla.org/ko/docs/Learn/HTML/Howto/%EB%8D%B0%EC%9D%B4%ED%84%B0_%EC%86%8D%EC%84%B1_%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0](https://developer.mozilla.org/ko/docs/Learn/HTML/Howto/데이터_속성_사용하기))

```
<h1>JavaScript Calculator</h1>
<p class="warning">Don't divide by zero</p>

<div id="calculator" class="calculator">

  <button id="clear" class="clear">C</button>

  <div id="viewer" class="viewer">0</div>

  <button class="num" data-num="7">7</button>
  <button class="num" data-num="8">8</button>
  <button class="num" data-num="9">9</button>
  <button data-ops="plus" class="ops">+</button>

  <button class="num" data-num="4">4</button>
  <button class="num" data-num="5">5</button>
  <button class="num" data-num="6">6</button>
  <button data-ops="minus" class="ops">-</button>

  <button class="num" data-num="1">1</button>
  <button class="num" data-num="2">2</button>
  <button class="num" data-num="3">3</button>
  <button data-ops="times" class="ops">*</button>

  <button class="num" data-num="0">0</button>
  <button class="num" data-num=".">.</button>
  <button id="equals" class="equals" data-result="">=</button>
  <button data-ops="divided by" class="ops">/</button>
</div>

<button id="reset" class="reset">Reset Universe?</button>
```



