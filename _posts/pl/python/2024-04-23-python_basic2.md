---
layout: post
bigtitle: "파이썬 기초 문법"
subtitle: "01. Python Basic"
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



## Python Grammer2 - 파이썬 문법2

---

이번 포스트에서는 Python 기초 문법을 통한 함수 사용법 등을 알아봅시다.

## 함수(Function)

프로그래밍의 기본 틀 
컴퓨터에게 정보 입력 --> 컴퓨터 작업 수행 --> 컴퓨터 작업 결과 출력

특정 기능을 수행하는 코드(들의 모임)
![그림1](/assets/img/pl/python/function_1.png)

내장함수, 사용자 지정 함수로 나뉨

- 내장함수
파이썬 개발자들이 이미 만들어 준 함수들, 편리하게 가져다 쓰면 됨
별도의 import가 따로 필요 없다
len(), int(), str(), print(), input() ... 등이 존재

- 사용자 지정 함수
사용자가 여러 코드를 묶어서 새로 만든 함수

```python
#사용법

def 함수이름(매개변수1, 매개변수2, ...):
    <수행할 명령>
    ...
    return 반환값

#def(ine) : 정의하다 키워드를 이용해서 함수 정의
#입구 = 매개변수 : 함수 내부로 값을 전달
#작용(기능) = 함수 속 명령 작성: 들여쓰기를 통해 명령 작성
#출구 = 함수 반환값 : return을 이용해서 함수 외부로 값을 전달

#반환이 필요한 이유
#전역변수, 지역변수의 개념
#전역변수의 경우 어디서든지 사용할 수 있는 변수, 함수 밖에서 정의된 변수
#지역변수의 경우 함수 안에서 정의된 변수, 변수를 정의한 범위에서만 사용 가능
#함수 내부에서 일어난 일은 함수 외부에서 알 수 없다 --> 반환을 통해 외부로 전달  
```

## 메서드(Method)
특정 자료에 대해 특정 기능(함수 수행)을 하는 코드
.append(), .count(), .pop(), .pow()

```python
import math
math.pow() #제곱 메서드
```

- 함수 vs 메서드
함수는 특정 기능을 한다, 매개변수를 이용하여 자료를 전달함
ex. len()

메서드는 특정 자료와 연관지어 기능을 함, 자료 뒤에 .을 찍어 사용함
ex. .append()

## 모듈(Module)
코드의 길이가 길어지고 모든 함수,변수를 구현하는 것은 불가능하고 누군가의 만들어 놓은 것을 활용하는 것이 필요로 모듈의 필요성 대두

특정 목적을 가진 함수, 자료의 모임

- 모듈 불러오기
```python
#사용법
#import(불러오다) 키워드를 이용하여 모듈 사용
import math
```

- 모듈 사용법 확인
모듈 속 함수/변수의 사용법을 확인 필요
```python
#사용법
import random
#range(start,stop) 중 한 원소를 가지고 옴
random.randrange(start, stop)
```

- 모듈 사용하기
.(dot)을 쓴 후에 모듈 속 함수/변수 사용

- 모듈 만들기
원하는 내용이 담긴 모듈 제작 가능
.py 파일로 만들 수 있음
```python
#사용법
#my_module.py 파일이 같은 경로에 존재해야함
import my_module

#.py 파일 생성 후 해당 파일에 함수 작성
#메인으로 쓰는 .py파일에서 import를 통해 불러오고 함수 작성 된 py파일이름.함수이름(매개변수)를 통해 작성
#import 함수작성 py파일 이름
#my_module.plus(a,b) my_module.py안의 plus 함수에 a,b를 넣어 값 출력
```
- 모듈 활용하기
```python
import math
import time
import random
from urlib.request import urlopen

#import는 해당 라이브러리,모듈을 불러옴
#from~import는 해당 라이브러리,모듈에서 하나의 함수를 불러옴
```


## 출력 - print()

원하는 정보나 자료를 컴퓨터가 출력

```python
#사용법

#1가지 자료형
print(내용) #str을 제외한 자료형
print("내용"), print('내용') #str형 "", ''로 내용을 감싸서 입력하여 출력

#두가지 이상의 자료형
#,(콤마)로 구분하여 출력, ,(콤마) 다음에는 공백이 필요
#서로 구분해야 함
print(내용, "내용", 6, ...)

#여러 번 사용하여 여러 줄에 걸쳐 출력 가능
#여러 줄에 걸쳐 사용 할 경우 이스케이프 시퀀스(Escape Sequence)로 별도의 처리 필요
print("\n") print("\t").... 
```

## 입력 - input()

정보를 컴퓨터에 전달
무엇을 입력하든 문자열로 입력 받아짐

```python
#사용법

#사용자가 전달한 값을 보관 필요 --> 변수 사용
var = input()
#터미널에 원하는 값 입력
#터미널 : 사람과 컴퓨터 간의 통로
```

## 자료형 확인 - type()

자료형을 알려줌

```python
#사용법

#type(변수 or 자료)
a = 10
print(type(a))
```

## 시퀀스 자료형
   순서가 있는 자료형
   ex. 문자열, 리스트, 튜플...
   
   - 특징
   1. 원소간의 순서가 존재 --> 인덱싱/슬라이싱이 가능
   인덱싱/슬라이싱 시 음수, 자리를 비우는 것도 가능
   2. 멤버 조회 : in 연산자로 시퀀스 안의 원소 확인 가능, True/False로 나타남
   3. 길이 확인 : len 연산자로 시퀀스 안에 원소가 몇 개인지 확인 가능
   4. 연결 연산 : + 연산자로 같은 시퀀스 2개를 이어 붙이기 가능
   5. 반복 연산 : * 연산자로 시퀀스를 반복 가능

   ```python
   #사용법

   list_a = [1,2,3,4,5]
   list_b = [6,7]

   print(list_a[1])

   if 1 in list_a: #True
    print("True")

   print(len(list_a)) #5

   print(list_a + list_b) #[1,2,3,4,5,6,7]

   print(list_b * 3) #[6,7,6,7,6,7]
   ```

## 문자열/시퀀스 자료형 접근방법

문자열과 시퀀스 자료형은 인덱스(index)라는 개념으로 접근할 수 있음
인덱스는 맨 앞에서부터 **0**부터 시작함
인덱싱, 슬라이싱의 개념으로 접근하여 자료형을 자르거나 합칠 수 있음

```python
#사용법

#인덱싱 : index를 이용해서 문자열이나 시퀀스 자료형의 특정 위치의 원소를 가져오는 방법
str_a = 'hi'
list_a = ["1", "2"]

#[]안에 인덱스 번호를 넣음
print(str_a[0]) #'h' 
print(list_a[0]) # "1"

#슬라이싱 : index를 이용해서 문자열이나 시퀀스 자료형의 일부분을 잘라서 가져오는 방법

str_a = "i am doctor"
list_a = ["1", "2", "3", "4"]

#빈칸도 인덱스 하나로 여김
#[시작인덱스 : 끝 인덱스] --> 시작부터 끝 인덱스-1의 값이 출력 
print(str_a[0:4])
print(list_a[1:3])
```

## 문자열/리스트 활용

시퀀스 자료형인 리스트를 가지고 추가, 삭제, 정렬 등을 할 수 있음
list안의 method를 사용

- 자료 추가 
1. list.append(자료 or 변수)
자료 또는 변수를 list의 마지막 원소 뒤에 추가, 오직 한 개의 자료만을 넣을 수 있음

2. list.insert(index, 자료 or 변수)
list의 index에 해당 자료 or 변수를 추가, 오직 한 개의 자료만을 넣을 수 있음

- 자료 삭제
1. list.remove(자료 or 변수)
처음 나오는 자료 or 변수를 제거, 중복이 있을 시 index가 작은 원소 제거
2. list.pop(index)
list의 index의 해당하는 원소를 제거 후 그 원소를 반환
괄호 안을 비울 시 마지막 원소로 적용

- 자료 정렬
1. list.sort()
list를 정렬, 숫자형은 오름차순, 문자열은 사전순으로 정렬
sort 사용시에는 리스트 내부의 자료형이 모두 동일해야 함, 다른 자료형끼리는 사용 불가능

- 자료 개수
1. seq.count(자료 or 변수)
시퀀스 내부의 자료 or 변수의 개수를 반환

- 자료 분할/쪼개기
1. str.split(기준 문자열)
기준 문자열을 기준으로 str문자열을 쪼개서 리스트로 반환
괄호 안을 비우면 공백으로 적용

- 자료 합치기
1. 합칠기준.join(시퀀스 자료형)
합칠기준을 기준으로 시퀀스 자료형을 합쳐서 문자열을 반환
괄호 안을 비울 시 공백으로 적용


```python
#사용법

list_a = [] #빈 리스트
a.append(10)
print(a) #[10]

list_b = [1,2,4,5]
list_b.insert(2, 3) #위치, 값
print(list_b) #[1,2,3,4,5]

list_c = [3,1,2,3]
list_c.remove(3)
list_c.pop(0) # 1이 제거, 1 반환
print(list_c) #[2,3]

list_d = [3,4,1,2,7,9,10]
list_e = ['carrot', 'apple', 'banana']
list_d.sort()
list_e.sort()
print(list_d, list_e) #[1,2,3,4,7,9,10], ['apple', 'banana', 'carrot']

list_f = [2,2,2,2,4,4,4,3,3]
print(list_f.count(2)) #4

str_g = "i a m"
print(str_g.split(" ")) #["i","a","m"]

list_h = ["h", "i"]
print('.'.join(list_h)) #h.i
```

## 딕셔너리 활용

- 자료 꺼내기
Dictionary[key] --> value

- 자료 추가
Dictionary[key] = value

- 자료 삭제
del Dictionary[key]



