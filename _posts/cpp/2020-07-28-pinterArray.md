---
title: Pointer and array
tag: cpp
---



## 포인터와 배열

### Similarities between pointers and fied arrays

**배열 변수는 마치 포인터인 것처럼 배열의 첫 번째 요소의 주소를 가지고 있다.** 다음 프로그램에서 이를 볼 수 있다.

C++에서 배열과 포인터가 같다고 생각하는 것은 일반적인 오류다. 두 요소 모두 배열의 첫 번째 요소를 가리키고 있지만, 형식 정보가 다르다. 위의 경우 `array`는 `int[5]`의 타입이고, 배열에 대한 포인터는 `int*` 타입이다.

포인터를 통해 배열의 모든 요소에 접근할 수 있지만, 배열 타입에서 파생된 정보(Ex. 배열 길이)는 포인터에서 접근할 수 없다.

대부분은 이를 통해 고정 배열과 포인터를 효과적으로 처리할 수 있다.

예를 들어, 배열을 역참조하여 첫 번째 요소의 값을 얻을 수 있다.

```cpp
int array[5] = { 9, 7, 5, 3, 1 };

// dereferencing an array returns the first element (element 0)
cout << *array; // will print 9!

char name[] = "Jason"; // C-style string (also an array)
cout << *name; // will print 'J'
```

실제로 배열 자체를 역참조하지는 않는다. 

(`int[5]` 타입의) 배열은 int 타입의 포인터로 암시적으로 변환되고 포인터를 역참조하여 포인터가 보유하고 있는 메모리의 주소의 값을 얻을 수 있다. (배열의 첫 번째 요소의 값)

또한, 배열을 가리키는 포인터를 지정할 수 있다.



### Differencees between pointers and fixed arrays





출처: https://boycoding.tistory.com/201?category=1009770 [소년코딩]