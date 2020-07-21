---
title: inheritance, overriㅇㅇㅇ
tag: cpp
---



# [상속, 오버라이딩](https://modoocode.com/209)

---

 이제 각각의 `Employee` 클래스를 만들었으니, 이 `Employee` 객체들을 관리할 수 있는 무언가가 있어야 겠지요? 물론 단순히 배열을 사용해서 사원들을 관리할 수 있겠지만, 불편합니다. 그래서 저는 `EmployeeList` 클래스를 만들어서 간단하게 처리하도록 할 것입니다.

우리는 다음과 같은 멤버 변수들을 이용해서 사원 데이터를 처리할 것입니다.

```cpp
int alloc_employee;        // 할당한 총 직원 수
int current_employee;      // 현재 직원 수
Employee **employee_list;  // 직원 데이터
```

언제나 동적으로 데이터를 할당하는 것을 처리하기 위해서는 두 개의 변수가 필요 했는데, 하나는 현재 할당된 총 크기고, 다른 하나는 그 중에서 실제로 사용하고 있는 양이지요. 이렇게 해야지만 할당된 크기 보다 더 많은 양을 실수로 사용하는 것을 막을 수 있습니다. 따라서 우리도 `alloc_employee` 가 할당된 크기를 알려주는 배열이고, `current_employee` 는 현재 `employee_list` 에 등록된 사원 수라고 볼 수 있지요.

`employee_list` 가 `Employee**` 타입으로 되어 있는 이유는, 우리가 이를 `Employee*` 객체를 담는 배열로 사용할 것이기 때문입니다. 그렇다면 `EmployeeList` 클래스의 생성자는 아래와 같이 쉽게 구성할 수 있겠지요.

```cpp
EmployeeList(int alloc_employee) : alloc_employee(alloc_employee) {
  employee_list = new Employee*[alloc_employee];
  current_employee = 0;
}
```

그리고 사원을 추가하는 함수는 아래처럼 단순하게 구성할 수 있습니다.

```cpp
void add_employee(Employee* employee) {
  // 사실 current_employee 보다 alloc_employee 가 더
  // 많아지는 경우 반드시 재할당을 해야 하지만, 여기서는
  // 최대한 단순하게 생각해서 alloc_employee 는
  // 언제나 current_employee 보다 크다고 생각한다.
  // (즉 할당된 크기는 현재 총 직원수 보다 많음)
  employee_list[current_employee] = employee;
  current_employee++;
}
```