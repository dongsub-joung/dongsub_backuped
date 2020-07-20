---
title: Function Overloading
tag: cpp
---



# [함수의 오버로딩](https://modoocode.com/188)

C++ 컴파일러에서 함수를 오버로딩하는 과정은 다음과 같습니다.

#### 1 단계

자신과 타입이 정확히 일치하는 함수를 찾는다.

#### 2 단계

정확히 일치하는 타입이 없는 경우 아래와 같은 형변환을 통해서 일치하는 함수를 찾아본다.

- `Char, unsigned char, short` 는 `int` 로 변환된다.
- `Unsigned short` 는 `int` 의 크기에 따라 `int` 혹은 `unsigned int` 로 변환된다.
- `Float` 은 `double` 로 변환된다.
- `Enum` 은 `int` 로 변환된다.

#### 3 단계

위와 같이 변환해도 일치하는 것이 없다면 아래의 좀더 포괄적인 형변환을 통해 일치하는 함수를 찾는다.

- 임의의 숫자(numeric) 타입은 다른 숫자 타입으로 변환된다. (예를 들어 `float -> int)`
- `Enum` 도 임의의 숫자 타입으로 변환된다 (예를 들어 `Enum -> double)`
- `0` 은 포인터 타입이나 숫자 타입으로 변환된 0 은 포인터 타입이나 숫자 타입으로 변환된다
- 포인터는 `void` 포인터로 변환된다.

#### 4 단계

유저 정의된 타입 변환으로 일치하는 것을 찾는다 (이 부분에 대해선 나중에 설명!)([출처](http://www.learncpp.com/cpp-tutorial/76-function-overloading/))

만약에 컴파일러가 위 과정을 통하더라도 일치하는 함수를 찾을 수 없거나 같은 단계에서 두 개 이상이 일치하는 경우에 **모호하다 (ambiguous)** 라고 판단해서 오류를 발생하게 됩니다.

```
void Date::ShowDate() {}
//Date:: 을 함수 이름 앞에 붙여주게 되면 
//이 함수가 "Date 클래스의 정의된 함수" 라는 의미를 부여하게 됩니다.
```

```cpp
class Date
{
	int year;
	int moth;
	int day;
	
	public:
		void setDate(int year, int month, int date);
};

//class의 정의와 본체는 분리하는 것이 일반적
//"Date 클래스의 정의된 함수" 라는 의미를 부여하게 됩니다. 
void Date::setDate(int y, int m, int d)
{
	year = y;
	month = m;
	day = d;
}
```

---

#### 생성자

```
Date day(2011, 3, 1);         // 암시적 방법 (implicit), 선호
Date day = Date(2012, 3, 1);  // 명시적 방법 (explicit)
```

