---
title: C++ 잡다
tag: cpp
---





## Boolean return values

부울 반환 값,

부울 값은 어떤 것이 참(true)인지 아닌지 확인하는 함수의 반환 값으로도 사용된다. 이러한 기능을 가진 함수의 이름은 일반적으로 is나 has로 시작한다.

---

## How do I do exponents?

C++에서는 거듭제곱 연산자를 지원하지 않는다.

C++에서 `^` 연산자는 비트 XOR 연산자(Bitwise XOR operation)다. 

C++에서 거듭제곱 연산을 실행하려면 `<cmath>` 라이브러리를 `#include`하여 `pow()` 함수를 사용하면 된다.

```cpp
#include <cmath>

double x = std::pow(3.0, 4.0); // 3 to the 4th power
```

`pow()` 함수의 매개 변수(parameter) 및 반환 값(return value) 모두 자료형이 `double`이다. 

이것은 거듭제곱 연산에서 밑(base)과 지수(exponentiation)를 부동 소수점 숫자로 가정한다. 때문에, 부동 소수점 숫자의 반올림 오류로 인해 결과가 정확하지 않을 수 있다.

---

## Increment/decrement operators

전위 증감 연산자(prefix increment/decrement operator)는 매우 간단하다. 증가 또는 감소한 다음 `x`값을 평가한다.

```cpp
int x = 5;
int y = ++x; // x는 이제 6과 같고, 6은 y에 할당된다.
```

후위 증감 연산자(postfix increment/decrement operator)는 조금 더 까다롭다. 컴파일러는 `x`의 임시 복사본을 만들고, 원본 `x`를 증가시키거나 감소시킨 다음 `x`의 임시 복사본을 평가한다. 그다음 `x`의 임시 복사본이 삭제된다.

```cpp
int x = 5;
int y = x++; // 5는 y에 할당되고, x는 이제 6과 같다.
```

전위 증감 연산자를 사용하는 것이 후위 증감 연산자를 사용하는 것보다 성능이 더 좋을뿐더러 이상한 문제에 부딪힐 가능성이 더 작다.



---

## Side effects

**'사이드 이펙트(side effect)'란 함수 또는 표현식이 특정 상태(Ex. 메모리에 저장된 정보)를 수정하거나 입력 또는 출력하거나 다른 함수를 호출하는 것을 말한다.**

###### 사이드 이펙트는 대부분 유용하다:

```cpp
x = 5;
++x;
std::cout << x;
```

위 예제에서 할당 연산자(`=`)는 `x`의 값을 변경하는 사이드 이펙트를 가진다. 명령문이 실행 완료된 후에도 `x`는 값이 5이다. 연산자 `++`는 `x`값을 증가시키는 사이드 이펙트가 있다. `x`의 출력은 콘솔을 수정하는 사이드 이펙트를 가진다.

**정의되지 않은 동작(undefined behavior)**이란 프로그래밍 언어에서 동작이 제대로 정의하지 않은 코드를 실행한 결과를 말한다.

> 사이드 이펙트가 적용된 변수를 한 명령문(statement)에서 두 번 이상 사용하지 않음으로써 모두 피할 수 있다.

---

## Conditional operators

##### sizeof operator

##### 조건부 연산자

| Operator    | Symbol | Form      | Operation                                                    |
| ----------- | ------ | --------- | ------------------------------------------------------------ |
| Conditional | ? :    | c ? x : y | If c is nonzero (true) then evaluate x, otherwise evaluate y |

조건부 연산자 `? :`는 C++의 유일한 삼항 연산자(피연산자가 3개)이기 때문에 '삼항 연산자'라고도 한다.

`? :` 연산자는 `if-else` 문을 더 간결하게 사용하는 방법을 제공한다.

```cpp
if(condition) expression;
else other_expression;

//다음과 같이 작성할 수 있다.
(condition)? expression : other_expression;
```

`? :` 연산자는 우선순위가 매우 낮다.

---

## Overloading

C++ 에서는 사용자 정의 연산자를 사용할 수 있습니다. 

본 연산자들을 직접 사용자가 정의하는 것을 연산자를 **오버로딩(overloading)** 한다고 부릅니다. 이전에 같은 이름의 함수를 인자만 다르게 사용하는 것을 '함수를 오버로딩 했다' 라고 불렀던 것 처럼, 기본 연산자를 여러분이 설계한 클래스에 맞게 직접 사용하는 것을 '연산자를 오버로딩 했다' 라고 부릅니다.

일단 연산자 오버로딩을 사용하기 위해서는, 다음과 같이 오버로딩을 원하는 연산자 함수를 제작하면 됩니다.

```
(리턴 타입) operator(연산자) (연산자가 받는 인자)
```

---

## Block

복합 명령문, Compound statement 한 명령문같이 보이는 명령문의 그룹. `{}`

```cpp
int add(int x, int y) 
{ // 시작 블록 (start a block) 
	return x + y; 
} // 끝 블록 (end a block)
```

---

## Local variables

## 