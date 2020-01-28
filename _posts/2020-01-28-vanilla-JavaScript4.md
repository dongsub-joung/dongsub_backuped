---
title: vanilla JavaScript (4)
tags: vanilla JS
---

파일 한번 날라감.

>  다 하면 항상 github에 푸쉬하자!

## [filter](https://niceman.tistory.com/77)

배열 처리 정리에 사용됨.

> Define

콜백함수에 지정된 조건에 맞는 요소를 새롭게 반환.

```js
	let date=[
        {name:"j", age: 20},
        {name:"k", age: 16},
        {name:"r", age: 27},
        {name:"m", age: 21},
        {name:"r", age: 19},
    ]
    // age가 20이상인 원소 추출 =필터링
    let result= data.filter(x =>{
        return x.age >= 20
    });
console.log(result);
```

> 3개의 원소를 반환해서 배열로 보여줌
>
> 테스트를 통과한 요소로 이루어진 새로운 배열. 어떤 요소도 테스트를 통과하지 못했으면 빈 배열을 반환합니다.

### 매개변수


- `callback`

  각 요소를 시험할 함수. `true`를 반환하면 요소를 유지하고, `false`를 반환하면 버립니다. 다음 세 가지 매개변수를 받습니다.

  ​	`element`처리할 현재 요소.

  ​    `index` Optional처리할 현재 요소의 인덱스.

  ​    `array` Optional`filter`를 호출한 배열.

- `thisArg` Optional

  `callback`을 실행할 때 `this`로 사용하는 값.
  
  

---

## [Math](https://m.blog.naver.com/PostView.nhn?blogId=diceworld&logNo=220174711730&proxyReferer=https%3A%2F%2Fwww.google.com%2F)

### floor

소수값이 존재할 때 소수값을 버리는 역활을 하는 함수

### ceil

 소수값이 존재할 때 값을 올리는 역활을 하는 함수=반올림

### round

소수값에 따라 올리거나 버리는 역활을 하는 반올림 함수



---

## css

### [z-index](https://www.codingfactory.net/10878)

> need why?

position 속성을 이용하면 요소를 겹치게 놓을 수 있기때문에 요소들의 수직 위치를 z-index 속성으로 정해야함.

값은 정수이며, 숫자가 클 수록 위로 올라오고, 숫자가 작을 수록 아래로 내려갑니다.

 z-index 속성이 없으면 0처럼 취급합니다.(z-index의 기본값은 auto입니다.)

> Define

 z-index는 형제 요소 간의 수직 위치를 정하고, 이 때 값이 없으면 0으로 처리합니다. 자식 요소는 부모 요소와 같이 움직입니다.



---

### opacity

> Define

요소를 투명하게 만드는 속성. 투명도를 정할 수 있음.

- 기본값 : 1
- 상속 : No
- 애니메이션 : Yes
- 버전 : CSS Level 3

> how to use?

opacity: number | initial | inherit

- number : 0.0부터 1.0까지의 수를 넣습니다.
- initial : 기본값으로 설정합니다.
- inherit : 부모 요소의 속성값을 상속받습니다.

숫자가 작을수록 투명해집니다. 



---

### [animation 과 @keyframes](https://webclub.tistory.com/621)

> 구성

1. 애니매이션을 나타내는 CSS style
2. 애니메이션의 중간 상태를 나타내는 keyframes

> 장점

애니메이션은 트랜지션보다 훨씬 더 규모가 크고 복잡하며 다양한 능력을 가지고 있기 때문에 좀 더 정밀한 효과를 구현할 수 있습니다.

> 기존에 사용되던 자바스크립트를 이용한 애니메이션과의 비교우위

- 자바스크립트를 모르더라도 간단하게 애니메이션을 만들 수 있습니다.
- 자바스크립트를 이용한 애니메이션은 잘 만들어졌더라도 성능이 좋지 못할때가 있습니다. CSS 애니메이션은 frame-skipping 같은 여러 기술을 이용하여 최대한 부드럽게 렌더링됩니다.
- 브라우저는 애니메이션의 성능을 효율적으로 최적화할 수 있습니다. 예를 들어 현재 안보이는 엘리먼트에 대한 애니메이션은 업데이트 주기를 줄여 부하를 최소화할 수 있습니다.

> #### @keyframes

`@keyframes` 를 타임라인 안의 하나의 스테이지(구간)들 이라고 생각하세요. `@keyframes` 안에서 우리는 스테이지들을 정의하고 각 구간마다 다른 스타일을 적용 시킬 수 있습니다.

_=시간 상의 순서로 보았을 때 애니메이션을 추가할 수 있다는 뜻으로 이해함_

다음으로 CSS 애니메이션이 작동하도록 `@keyframes` 를 선택자로 묶어주세요. 이것은 마지막에 @keyframes 선언 안의 모든 코드를 분석하고 초기의 스타일을 각 스테이지에 따라 새로운 스타일로 변경시킬 것입니다.

> #### ainmation-timing-function

애니메이션 속도 조절 

 *linear | ease | ease-in | ease-out | ease-in-out | cubic-bezier* 

```css
.bgImage{
	animation: fadeIn .5s linear;
}
```

+[CSS 애니메이션 초보자 입문서](https://webdesign.tutsplus.com/ko/tutorials/a-beginners-introduction-to-css-animation--cms-21068)



---

### [position](https://www.zerocho.com/category/CSS/post/5864f3b59f1dc000182d3ea1)

> #### absolute

relative가 static인 상태를 기준으로 주어진 픽셀만큼 움직였다면, absolute는 **position: static 속성을 가지고 있지 않은 부모를 기준**으로 움직입니다. 만약 부모 중에 포지션이 relative, absolute, fixed인 태그가 없다면 가장 위의 태그(body)가 기준이 됩니다.

```css
.bgImage{
    position: absolute;
}
```

클론 만들기에서 사용된 `absolute`만 알아봄



---

