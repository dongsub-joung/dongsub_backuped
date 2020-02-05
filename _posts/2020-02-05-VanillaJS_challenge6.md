---
title: VanillaJS Challenge (6)
tag: VanillaJS Challenge
---



## 조건

_Make a number guessing game using Javascript!_

1. Find a random number on a range between 0 and a number defined **by the user**.
2. Use **range** input.
3. Update the range value in **real time**.
4. **Only** play after the user chooses a number.
5. Notify the user if the game is lost or won.
6. Don't give up.

   

> 조건되는 것들

+ 사용자가 숫자를 입력해서 컴퓨터가 그것을 맞추면 이기고, 못맞추면 지는 게임.
+ 숫자의 범위는 `바`로 이동(=변화)시킬 수 있음
+ 몇번이고 재도전 가능



---

## 알고리즘

숫자 찾는 게임 응용? C언어로 만들어본 적있음

> 생각

+ 랜덤한 정수 생성하기

  `random()*130` 인데 아마 ? c처럼 패턴 있는 랜덤 숫자라서 시간 변수를 연동해야함.

  `range` 사용

+ `real time`으로 범위값을 업뎃

  ?

  `toggle` 이용해서 이전 함수를 제거하고 추가? 

+ 결과 text 만들기

  `if else`

+ 스크롤 바를 만들어야 함.



---

## 정보 수집

### [Range](https://developer.mozilla.org/ko/docs/Web/API/Range)

The **`Range`** interface represents a fragment of a document that can contain nodes and parts of text nodes.

> `interface` _represents a fragment document_  

A range can be created by using the [`Document.createRange()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/createRange) method. Range objects can also be retrieved by using the [`getRangeAt()`](https://developer.mozilla.org/en-US/docs/Web/API/Selection/getRangeAt) method of the [`Selection`](https://developer.mozilla.org/en-US/docs/Web/API/Selection) object or the [`caretRangeFromPoint()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/caretRangeFromPoint) method of the [`Document`](https://developer.mozilla.org/en-US/docs/Web/API/Document) object.

> `creat`: _Document.createRange()_
>
> `retrieve`: _selection.getRangeAt()  OR  document.caretRangeFromPoint()_

_`HTML` input type="range" 존재함. 내가 찾던건 이거였음_

   

[Math.random](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)

The **`Math.random()`** function returns a floating-point, pseudo-random number in the range 0 to less than 1 (inclusive of 0, but not 1) with approximately uniform distribution over that range — which you can then scale to your desired range. The implementation selects the initial seed to the random number generation algorithm; it cannot be chosen or reset by the user.

> `function `: _returns a floating-point, pseudo-random number_
>
> `implementation`:  _the random number generation algorithm_

​    

### [Input Number value Property](https://www.w3schools.com/jsref/prop_number_value.asp)

```js
//Example
document.getElementById("myNumber").value = "16";

//Return the value property:
numberObject.value

//Set the value property:
numberObject.value = number
```

​    

### [input type="number"](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number)

`<input>`elements of type **`number`** are used to let the user enter a number. They include built-in validation to reject non-numerical entries. The browser may opt to provide stepper arrows to let the user increase and decrease the value using their mouse or by simply tapping with a fingertip.

> `input element`

### [input type="button"](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button)

```js
//A simple button
const button = document.querySelector('input');
const paragraph = document.querySelector('p');

button.addEventListener('click', updateButton);

function updateButton() {
  if (button.value === 'Start machine') {
    button.value = 'Stop machine';
    paragraph.textContent = 'The machine has started!';
  } else {
    button.value = 'Start machine';
    paragraph.textContent = 'The machine is stopped.';
  }
}
```



### [Node.textContent](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)

The `textContent` property of the [`Node`](https://developer.mozilla.org/en-US/docs/Web/API/Node) interface represents the text content of the node and its descendants.

> `property` :   _represents the text_

```js
let text = someNode.textContent;
someOtherNode.textContent = string;
```

> `Return value` : A string or null
>
> `Differences From innerText`
>
> `Differences from innerHTML`

   

### [input type range 슬라이더 value 값 실시간표시, oninput](https://doolyit.tistory.com/52)

```js
//1차 도전
//range 값조정
let rangeScroll= document.getElementById("rangeScroll");
let selectedNum= document.querySelector(".selectedNum");
document.getElementById("rangeScroll").setAttribute("max", 100);
let max = document.getElementById("rangeScroll").getAttribute("max");

// 범위 max를 연동해야 함 =max값을 변동시켜야함.
function changeRange(max){
    selectedNum =`Generate a number beween 0 and ${max}`;
    return selectedNum.textContent;
}

//2차 도전
let rangeScroll= document.getElementById("rangeScroll");
let oniputVal= rangeScroll.innerHTML;
function change(){
    rangeScroll.setAttribute("oninput", `${oniputVal}=this.value`);
}
function showSliderValue(val){
    const valueView= document.getElementById("sliderValueView");
    valueView.innerHTML= `${val}`;
}
```

   

[html에서 range를 이용해서 input을 받고 input 변화값 보여주기.](https://frhyme.github.io/html/html_range_oninput/)

```html
<input type="range" name="points" min="0" max="1.0" step="0.05" value="0" oninput="document.getElementById('value1').innerHTML=this.value;">
```

```js
//html말고 js로 정리해서 입력
const sliderValueView= document.getElementById('sliderValueView');
const rangeScroll= document.getElementById(`rangeScroll`);
rangeScroll.setAttribute("oninput", "sliderValueView.innerHTML=rangeScroll.value");
```



