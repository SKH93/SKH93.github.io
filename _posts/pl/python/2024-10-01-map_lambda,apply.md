---
layout: post
bigtitle: "파이썬 map, lambda, apply, filter 함수"
subtitle: "03. Python map, lambda, apply, filter 사용"
categories:
    - programming language
    - python
# tags:
#   - python
#   - programming language
#   - basic
comments: true
# related_posts:
#    -
#    - 
published: true
---


## Python map, lambda, apply, filter 함수 사용

---

이번 포스트에서는 Python에서 자주 사용하고 유용한 함수인 map(), lambda(), apply() 사용을 다루겠습니다.


## map

* 특징

1. 지연평가(lazy Evaluation) 방식 
    - 필요한 시점까지 연산을 늦추는 방식, 불필요한 연산을 최소화하여 성능을 향상시키는 방법
    - 각 요소에 대해 함수를 적용하여 새로운 iterable 객체를 생성하지만 이 과정에서 실제로 변환된 결과값들이 생성되는 것이 아니라, 필요할 때까지 기다리는 것임
    - 변환된 결과값들이 모두 메모리에 저장되지 않고 부부만 계산하여 처리할 수 있기에 불필요한 메모리 사용 줄임

2. 간결성, 가독성
    - 코드의 간결성, 가독성 상승

3. 성능
    - C로 구현되어 있어 일반적인 for문 보다 더 빠른 실행 속도를 제공함

4. 메모리 사용량
    - 새로운 리스트 생성하지 않고, iterator 객체를 반환하므로, 메모리 사용량을 최소화할 수 있음
    - 매우 큰 iterator의 처리의 경우, 메모리 사용량이 매우 높아질 수 있음

5. 제약사항
    - 입력된 파라미터의 모든 iterator 객체의 길이가 같아야 함

**✅ 기본 문법**

> **map(function, iteration)**<br>

*function : 각 요소에 적용할 함수 이름*<br>
*iteration : 함수를 적용할 데이터 집합*<br>

type : map타입

**✅ 활용 문법**

> **map(function, iteration1, iteration2 ...)**<br>

*function : 각 요소에 적용할 함수 이름*<br>
*iteration1, iteration2 ... : 함수를 적용할 데이터 집합*<br>

```python
#1. sequence형 제곱을 list로 반환
def square(x):
    return x ** 2

numbers = [1, 2, 3, 4, 5]
squared_numbers = map(square, numbers)
print(list(squared_numbers)) #[1,4,9,16,25]

#sequence형끼리 더한 값을 list로 반환
def add(x,y):
    return x + y
number1 = [1, 2, 3, 4, 5]
number2 = [10, 20, 30, 40, 50]
added_numbers = map(add, numbers1, numbers2)
print(list(added_numbers)) #[11, 22, 33, 44, 55]


#정수 타입으로 변환
list(map(int, [1.1, 2.2, 3.3])) #[1, 2, 3]
```

## lambda

람다함수는 익명함수(Anonymous function)라고 불림
간단한 한 줄 짜리 함수를 정의할 때 사용
주로 filter(), map(), sorted() 등의 함수와 함께 사용, 인자로 전달됨


*특징
1. 메모리 절약
2. 코드의 간결함
3. 함수의 이름이 없음
4. 표현식 하나만 사용 가능

![lambda와 함수](/assests/img/pl/python/lambda1.png)

**✅ 기본 문법**
> **lambda arguments : expression**<br>
*arguments : 매개변수, 인자*<br> 
*expression : 표현식*

**✅ 활용 문법**

1. map()과 활용

```python
list(map(lambda x: x**2, range(5)))
#[0, 1, 4, 9, 16]
```
2. reduce()와 활용

```python
from functools import reduce
reduce(lambda x:y x+y, )
```
