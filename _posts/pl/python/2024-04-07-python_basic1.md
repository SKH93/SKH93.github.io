---
layout: post
bigtitle: "파이썬 기초"
subtitle: "01. python basic"
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



## Python Grammer - 파이썬 문법

---

이번 포스트에서는 2024년 기준 가장 많이 사용하는 프로그래밍 언어인 Python(파이썬)에 대해 알아보겠습니다.<br>

참고 사이트 : 

> TIOBE Index : [TIOBE Index](https://www.tiobe.com/tiobe-index/)
>
> Pypl Index : [Pypl Index](https://pypl.github.io/PYPL.html)

![그림1](/assets/img/pl/python/pl_ref_1.png)

![그림2](/assets/img/pl/python/pl_ref_2.png)

## Programming Language(프로그래밍 언어)

---

프로그래밍 언어, 고급언어

- 정의 : 프로그램을 만들기 위해 언어와 통신하는 은어<br>

프로그래밍

- 정의 : 프로그램을 만드는 작업,  컴퓨터에게 일을 시키는 방법<br>

프로그래밍 실행과정

![그림3](/assets/img/pl/python/pl_execute_1.png)

**파이썬**

- 프로그래밍 언어 중 하나
- Guido Van Rossum에 의해 개발됨
  - 1989년 시작해서 1991년 첫번째 릴리즈
- 특징
  - 읽기 쉽고 간결한 문법
  - 풍부한 표준 라이브러리 장착
  - 높은 이식성 및 확장성
  - 대화식 인터프리터
  - 사용 : 웹, 데이터 분석, 인공지능 ... 등 다양한 분야에서 사용



## Basic Data Type(기초 자료형)

---

1. **숫자형(Number)**

   - 숫자로 이루어진 자료형

   - 정수(Integer) : int

   - 실수(Float) : float

     > 6, 10
     >
     > 6.5, 3.1111223344
     >
     > 10e-4, 10e3

2. **문자형(String)**

   - 문자, 문자열로 이루어진 자료형

   - 아래의 시퀀스 자료형에도 속함

   - 큰따옴표(""), 작은 따옴표('')로 구분, 같은 문자기 기호로 열거나 닫아야 함

   - 여러줄을 나타날 때는 (""" """) 또는 (''' ''')으로 나타냄

     > 'h', 'i go home', 'alphabet'
     >
     > """
     >
     > hello, world!
     >
     > go python
     >
     > """
     >
     > '''
     >
     > this is python
     >
     > go python
     >
     > '''

3. **복합 자료형**, **시퀀스 자료형**

   - 여러 자료를 보관하는 자료형, 다른 종류의 자료를 함께 담을 수 있음

   1. **리스트(List)** : [], 자료 안에 순서가 존재

      >  [], ['a', 'b'], [1,'a','b'], [1, ['a',2]]

   2. **튜플(Tuple)** : (), 값 변경 불가, 자료 안에 순서가 존재

      > (1,2,3), ('a','b','c')

   3. **집합(Set)** : {}, 중복 값 없음, 자료 안에 순서가 *없음*

      > {1,2,3}, {'a','b','c'}

   4. **딕셔너리(Dict)** : {}, set와 기호가 같음, key와 value의 쌍으로 이루어짐

      > {'name' : 'toy', 'age' : 30}

4. **불형(Boolean)**

   - True, False 둘 중 하나의 값을 가짐

cf. 주석(Comment)

- 컴퓨터가 실행시키지 않고 무시함

- 한 줄 주석 #, 여러 줄 주석 """ """, ''' '''로 표현

  > #한 줄 주석
  >
  > """
  >
  > 여러 줄 주석
  >
  > 여러 줄 주석
  >
  > """

#### 연산(Operation)

1. 사칙 연산
   - 숫자형 자료 : +, - , *, /
2. 특수 연산
   - 숫자형 자료 : //(몫 연산자), %(나머지 연산자), **(제곱 연산자)
3. 문자형 자료 연산
   - +(이어붙이기), *(반복하기)
4. 논리 연산
   - and(&), or(|), not(!)
   - True, False로 값이 반환
5. 비교 연산
   - \>, \<, \>=, \<=, ==(같다), !=(같지 않다)
   - True, False로 값이 반환

```python
print(3+5) #8
print(3-5) #-2
print(3*5) #15
print(3/5) #0.6

print(13//5) #2
print(13%5) #3
print(2**4) #16

print("안녕" + "하세요") #안녕하세요
print("안녕"*3) #안녕안녕안녕
```

#### 형 변환(Casting)

바꿀자료형(바뀔변수 또는 바뀔자료)

```python
int(6.3) #6
float(6) #6.0
str(6) #'6'

a = 6
print(int(a)) #6
print(float(a)) #6.0
print(str(a)) #'6'

b = (1,2,3)
print(list(b)) #[1,2,3]
print(set(b)) #{1,2,3}
print(tuple(b)) #(1,2,3)
```



## Variable(변수)

자료를 어떤 그릇에 담아 보관한다고 하자. 해당 그릇을 변수라고 한다.

*변수 이름 = 자료*

```python
#변수 이름 = 자료
#= : 대입

#a의 변수에 6을 대입한다
a = 6
```

- 변수 이름의 규칙이 존재함
  1. 숫자, 알파벳, 한글, 언더바(_) 등을 사용 가능
  2. 숫자로 시작하면 안됨
  3. 숫자로만 구성된 변수 이름 금지
  4. 파이썬 예약어(keyword) 사용 금지
  5. 공백문자()와 연산자(+,-,%..등) 사용 금지



## Control Statement(제어문)

---

조건문(Conditional Statement), 반복문(Repetitive Statement)이 존재

#### Conditional Statement(조건문)

조건이 True일 때 해당 문을 수행

조건에 따라서 분기가 나눠지는 경우 존재

어떠한 특정 조건에 따라서 실행되는 명령이 달라지는 구문

1. if문
   - if 
   - if ~ else
   - if ~ elif ~ else

들여쓰기 시 Tab 이용, 내어쓰기 시 shift+Tab 이용

```python
#조건1이 True일 때 해당 문을 수행
if 조건1:
___수행할 명령(들여쓰기 필요함)

#조건1이 True일 때 if문 수행, 조건1이 False일 때 else문 수행
if 조건1:
___수행할 명령(들여쓰기 필요함)
else:
___수행할 명령(들여쓰기 필요함)

#조건1이 True일 때 if문 수행
#조건1이 False, 조건2가 True일 때 elif문 수행
#조건1이 False, 조건2도 False일 때 else문 수행
#elif의 경우 여러개 쓸 수 있음
if 조건1:
___수행할 명령(들여쓰기 필요함)
elif 조건2:
___수행할 명령(들여쓰기 필요함)
else:
___수행할 명령(들여쓰기 필요함)
```



#### Repetitive Statement(반복문)

어떠한 조건이나, 범위 내에서 어떠한 명령을 반복적으로 수행

1. for문

```python
for 변수 in 시퀀스:
___수행할 명령(들여쓰기 필요함)

for i in [1,2,3]:
    print(i)
#1
#2
#3
```



2. while문

   - 조건이 True일 때 수행, 조건이 False일 때 수행하지 않음

     ※ 주의점 : 조건이 항상 True일 때, **무한루프**가 되는 것을 주의

```python
while(조건):
___수행할 명령(들여쓰기 필요함)

a = 0
while(a<5):
    print(a)
    a = a + 1 #a += 1과 동일
#0
#1
#2
#3
#4
```

