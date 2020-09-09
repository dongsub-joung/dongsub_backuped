---
title: Vue style bind
tag: VueJS
---



 데이터 바인딩은 엘리먼트의 클래스 목록과 인라인 스타일을 조작하 기 위해 일반적으로 사용됩니다. 이 두 속성은 `v-bind`를 사용하여 처리할 수 있습니다. 우리는 표현식으로 최종 문자열을 계산하면 됩니다. 

 그러나 문자열 연결에 간섭하는 것은 짜증나는 일이며 오류가 발생하기 쉽습니다. 이러한 이유로, Vue는 `class`와 `style`에 `v-bind`를 사용할 때 특별히 향상된 기능을 제공합니다. 표현식은 문자열 이외에 객체 또는 배열을 이용할 수 있습니다.

```html
<!--html-->
<div
     class="static"
     v-bind:class="{ active: isActivae, 'text-danger': hasError }"
></div>
```

```
//js
data:{
	isActive: true,
	hasErro: false
}
```

```html
<!-- html, 랜더링 -->
<div class="static active">
</div>
```

`isActive` 또는 `hasError` 가 변경되면 클래스 목록도 그에 따라 업데이트됩니다.

- 바인딩 된 객체는 인라인 일 필요는 없습니다.

```html
<!--html-->
<div v-bind:class="classObject">
</div>
```

```javascript
//JS
data: {
    classObject: 
    {
         active: true,
        'text-danger': false       
    }
}
```

- 또한 객체를 반환하는 [계산된 속성](https://kr.vuejs.org/v2/guide/computed.html)에도 바인딩 할 수 있습니다. 

```javascript
// <!-- html -->
// <div v-bind:class="classObject"></div>

// new Vue ...
data: {
    isActive: true,
        error: null
},
computed: {
    classObject: function () 
    {
        return 
        {
            active: this.isActive && this.error,
                'text-danger': this.error && this.error.type === 'fatal'
        }
    }
}
```







