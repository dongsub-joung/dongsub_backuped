---
title: VanillaJS Challenge (4)
tag: VanillaJS Challenge
---



> **Events, localStorage**

## 조건

1. Save the country selection to localStorage.
2. Load the saved selection on refresh.

**Clues:**

- Don't forget to add '**values**' to the options.
- You need to **'select'** the option that has the same value as the localStorage.
- [< select >](https://developer.mozilla.org/ko/docs/Web/API/HTMLElement/change_event)
- [< option >](https://developer.mozilla.org/ko/docs/Web/HTML/Element/option)
- [.querySelector()](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelector) (Check out the section: 좀 더 복잡한 선택자)



---

## 알고리즘

1. `document.body` 변수화

2. `innerHTML`로 박스 생성 (여러 선택자를 선택하는 박스가 있던걸로 기억)

3. if `localStorage`에 값이 `null`이면 선택창,

   else 값이 존재하면 선택된 값을 저장.

4. `JSON`으로 저장된 오브젝트를 문자열로 변환

   로드 할때는 역으로 변환



---

## 실행



