---
title: VanillaJS Challenge (4)
tag: VanillaJS Challenge
---



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

## 













































----

## 실행

html의 `select-option`은 자동으로 값을 반환하지 않았음. 

>  [셀렉트 박스의 옵션 값과 텍스트 값 가져오기](https://frhyme.github.io/web/html_select_javascript/)

```js
<script>
        var alert_select_value = function (select_obj){
            // 우선 selectbox에서 선택된 index를 찾고 
            var selected_index = select_obj.selectedIndex;
            // 선택된 index의 value를 찾고 
            var selected_value = select_obj.options[selected_index].value;
            // 원하는 동작을 수행한다. 여기서는 그냥 alert해주는 식으로만 처리함. 
            alert(selected_value);
        };
    </script>
```



