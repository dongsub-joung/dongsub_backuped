---
title: JS DOM Function
tag:JS
---

## Document Object Module

> html 파일 안의 모든 것을 Object로 만들어 우리가 JS로 html을 조종 할 수 있게 만들어준다. (=우리가 JS로 html을 조종할려면 모든것을 오브젝트로 만들 필요성이 있다. ) 

​	오브젝트 안에는 매우 많은 함수가 포함되고, 기본적으로 자바가 사용자를 위해 만들어져 있는 함수는 메소드라고 불림.(표준적인 JS양식인듯?) 

+ ​	doc은 html의 전체를 반환한다.



## Object

```
Object ={
	function 함수 = { },
	배열=[ ],
	변수={ },
	등등
}; 	//가능  
```



## console.dir

```js
const idName= document.getElementById("idName");
console.dir(idName);
```

​	크롬 콘솔창에서 확인해보면 `idName`의 모든 가능한 것들(=이벤트)이 나옴. html을 조종할 수 있음.



## querySelector

```js
오브젝트.querySelector(".className");
오브젝트.querySelector("#idName");
```

​	[특정 CSS 선택자를 가진 첫 번째 요소를 선택하는 메서드](https://www.codingfactory.net/10410)

+ querySelectorAll 

   [특정 CSS 선택자를 가진 모든 요소 선택하는 메서드](https://www.codingfactory.net/10413) 

  배열을 만들어서 이용함.(반복문 가능)







## 기타 

```js
window.addEvenListner("resize",functionName()); //바로 실행
window.addEvenListner("resize",functionName); //필요할 때 함수가 실행
```

 우리는 조건을 거는 입장이니까 필요할 때 함수가 실행되도록 하자.