---
layout: post
bigtitle: "파이썬 내장 라이브러리&함수"
subtitle: "02. Python Inner Function&Library"
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


## Python Inner Function&Library

---

이번 포스트에서는 코딩테스트에 정말 필요한 파이썬의 내부 라이브러리 및 함수에 대해 알아보겠습니다.<br>
현재 총 71개의 내장함수 존재

참조 사이트 : 
> python 공식문서 : [Python Inner Function](https://docs.python.org/ko/3/library/functions.html#anext)

> Python 버전 : 3.12.6 기준

## Python Inner Function

- abs(x) : 절대값을 반환<br>

인수 : 정수, 부동 소수점 숫자, 객체<br>
복소수 -> 크기 반환<br>

```python
#__abs__()
b = 7.1
c = -7.1

print(abs(b)) #7
print(abs(c)) #7
```

- aiter(async_iterable) : 비동기 반복 가능한 객체에 대해 비동기 반복자 반환

```python
# x.__aiter__()
# python 버전 3.10부터 추가
#동기적 반복 시 다음 작업 시 이전 작업이 완료될 때까지 블록하거나 기다림
#비동기 함수 사용 시 이전 작업의 완료 유뮤와 상관 없이 다른 작업 가능

#class 예시
import asyncio
class AsyncIterator:
   def __init__(self, data):
      self.data = data
      self.index = 0

   def __aiter__(self):
      return self

   async def __anext__(self):
      if self.index == len(self.data):
         raise StopAsyncIteration
      value = self.data[self.index]
      self.index += 1
      return value

async def main():
   async_iter = AsyncIterator([18, 19, 10, 11])
   async for value in aiter(async_iter):
      print(value)
        
asyncio.run(main())

#함수 예시
import asyncio
async def aiter(iter):
   for item in iter:
      yield item

async def sumOfnum(iter, start=0):
   async for x in aiter(iter):
      start += x
   return start

async def main():
   numerics = [4, 12, 20, 13, 15]
   total = await sumOfnum(numerics)
   print(f"The sum of the numbers is {total}")

asyncio.run(main())
```

- all(iterable) : iterable 모든 요소가 참(iterable이 비어있으면)이면 True, 아니면 False

```python
def all(iterable):
    for element in iterable:
        if not element:
            return False
    return True
```

- awaitable anext(async_iterator), awaitable anext(async_iterator, default)
: 대기 시 지정된 비동기 반복자에서 다음 항목 반환하거나, 지정된 경우와 반복자가 모두 소진된 경우 기본값을 반환함

next() 내장 함수의 비동기 변형 -> 비슷하게 동작<br>
async_iterator __anext__()의 메서드 호출 -> awaitable 반환<br>
기다리면 반복자의 다음 값이 반환됨<br>
default가 주어지면 반복자가 고갈되면 반환, 그렇지 않으면 StopAsyncIteration 발생<br>

```python
#python 버전 3.10 부터 추가
#예시 필요
```

- any(iterable) : iterable의 요소 중 하나라도 참이면 True, iterable이 비어 있으면 False를 돌려줌

```python
def any(iterable):
    for element in iterable:
        if element:
            return True
    return False
```

- ascii(object) : 인쇄 가능한 표현 포함한 문자열 반환, 이스케이프를 사용한 repr() 반환된 문자열의 비 ASCII 문자를 이스케이프함

```python
ascii()
```

- bin(x) : 10진수를 2진수로 반환, 앞에 '0b'가 붙음, String으로 반환

x가 정수가 아니면 __index__() 메서드를 통해 정수 반환<br>

```python
bin(3) #'0b11'
bin(-10) #'-0b1010'
```

- bool() : True, False 반환

class bool(object=False, /)<br>

```python
#python 3.7에서 변경
#파라미터가 지금 오직 위치

bool(True)

```

- breakpoint(*args, **kws) : 디버거로 이동

```python
#python 3.7에서 추가
#sys.breakpointhook() 참조
```

- bytearray() : 새로운 바이트 배열을 돌려줌, 0~255사이
class byterarray(source=b'') : 정수 시 배열이 그 크기를 갖고, 널 바이트로 초기화됨<br>
class bytearray(source, encoding) : 문자열 시 encoding 매개변수 반드시 필요<br>
class bytearray(source, encoding, errors)<br>

bytes() : 0~255사이 변경 불가능한 정수 시퀀스 bytes 객체 반환<br>
class bytes(source=b'')<br>
class bytes(source, encoding)<br>
class bytes(source, encoding, errors)<br>

bytearray()와 거의 동일<br>

- callable(object) : 객체 인수가 호출 가능하면 True, 아니면 False

class에서는 __call__() 함수와 동일<br>

```python
#python 3.0에서 제거 후 3.2에서 다시 도입
```

- chr(i) : ascii에서 숫자를 문자열로 돌려줌

```python
#0~114111(16진수 : 0x10FFFF 까지)
#범위 밖 : ValueError 발생
chr(97) #'a'
```

- classmethod() : 메서드를 클래스 메서드로 변환

```python
#python 3.9에서 변경
#python 3.10에서 변경
#python 3.11에서 변경
#@ : 데코레이터(decorator)
class C:
    @classmethod
    def f(cls, arg1, arg2): ...
```

- compile(source, filename, mode, flags=0, dont_inherit=False, optimize=-1) : 컴파일 수행

```python
#python 3.2에서 변경
#python 3.5에서 변경
#python 3.8에서 추가
```

- complex() : 복소수 나타냄

class complex(number=0, /)<br>
class complex(string, /)<br>
class complex(real=0, imag=0)<br>

```python
#python 3.6에서 변경
#python 3.8에서 변경
complex('+1.23') #1.23+0j
complex('-4.5j') #-4.5j
complex('-1.23+4.5j') #-1.23+4.5j
complex('\t( -1.23+4.5J )\n') #-1.23+4.5j
complex('-Infinity+NaNj') #-inf+nanj
complex(1.23) #1.23+0j
complex(imag=-4.5) #-4.5j
complex(-1.23, 4.5) #-1.23+4.5j
```

- delattr(object, name) : setattr()과 관련, 삭제

```python
delattr(x, 'foobar') == del x.foobar 
```

- dict() : 딕셔너리로 변환

class dict(**kwarg)<br>
class dict(mapping, **kwarg)<br>
class dict(iterable, **kwarg)<br>

- dir() : 인자가 없으면 현재 지역 스코프에 있는 이름들 리스트 돌려줌, 있으면 해당 객체에 유효한 attribute 리스트를 돌려줌 

dir()<br>
dir(object)<br>

```python
import struct
dir()   # show the names in the module namespace  
['__builtins__', '__name__', 'struct']
dir(struct)   # show the names in the struct module 
['Struct', '__all__', '__builtins__', '__cached__', '__doc__', '__file__',
 '__initializing__', '__loader__', '__name__', '__package__',
 '_clearcache', 'calcsize', 'error', 'pack', 'pack_into',
 'unpack', 'unpack_from']
class Shape:
    def __dir__(self):
        return ['area', 'perimeter', 'location']

s = Shape()
dir(s)
['area', 'location', 'perimeter']
```

- divmod(a,b) : 두 개의(복소수가 아닌)정수를 나누서 몫,나머지로 구성된 숫자 쌍 반환

```python
divmod(10,4) #(2, 2)
```

- enumerate(iterable, start=0) : 열거 객체 돌려줌

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
list(enumerate(seasons))
#[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
list(enumerate(seasons, start=1))
#[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]


def enumerate(iterable, start=0):
    n = start
    for elem in iterable:
        yield n, elem
        n += 1
```

- eval(expression, globals=None, Locals=None) : python 표현으로 파싱

```python
x = 1
eval('x+1') #2
```

- exec(object, globals=None, locals=None, /, *, closure=None) : python 코드의 동적 실행 지원

- filter(function, iterable) : 함수를 사용하여 iterable에서 만족하는 값을 반환

```python
def FilterFunc(num):
    return num > 40

num_list = [10,20,30,40,50,60,70,80]
filter_list = list(filter(FilterFunc, num_list))
print(filter_list) #[50,60,70,80]


filter_list = list(filter(lambda n : n > 40, num_list))
print(filter_list) #[50,60,70,80]
```

- float() : 실수로 변환

class float(number=0.0, /)<br>
class float(string, /)<br>

```python
#python 3.6에서 변경
#python 3.7에서 변경
#python 3.8에서 변경

float(3) #3.000000
float('3') #3.000000
```

- format(value, foramt_spec='') : value를 format_spec을 통하여 포맷팅 나타냄

```python
#python 3.4에서 변경
format(1, '')
```

- frozenset(iterable=set()) : 새 frozenset을 돌려줌

- getattr() : object의 이름 속성의 값 돌려줌

class getattr(object, name)<br>
class getattr(object, name, default)<br>

```python
getattr(x, 'foobar') == x.foobar
```

- globals() : 전역 변수

```python
a = 5
globals(a) #모듈 네임스페이스를 구현하는 사전을 반환함 
```

- hasattr(object, name) : name이 object의 속성 중 하나면 True, 아니면 False 반환

- hash(object) : 객체의 해시값을 돌려줌

- help() : 내장 도움말 시스템

- hex(x) : 10진수를 16진수로 변환

```python
hex(255) #'0xff'
hex(-42) #'-0x2a'
```

- id(object) : 객체의 아이덴티티를 돌려줌

- input() : prompt 인자 존재 시 끝에 개행문자를 붙이지 않고 표준 출력에 씀

class input()<br>
class input(prompt)<br>

```python
input("-->")
```

- int() : 정수로 반환

class int(number=0, /)<br>
class int(string, /, base=10)<br>

```python
int(3.14) #3
```

- isinstance(object, classinfo) : object 인수가 classinfo 인수의 인스턴스이거나 해당 하위 클랫의 인스턴스 인 경우 True를 반환, 아닌 경우 False 반환

- issubclass(class, classinfo) : class가 classinfo의 하위 클래스인 경우 True 반환

- iter(object) : 반복자 객체를 반환

class iter(object)<br>
class iter(object, sentinel)<br>

- len(s) : 객체 길이 반환

```python
s = [1,2,3,4]
print(len(s)) #4
```

- list() : 리스트로 반환

- locals() : 현재 지역 심볼 테이블을 나타내는 딕셔너리를 갱신하고 돌려줌

- map(function, iterable, **iterables) : iterable에 함수를 적용시켜 반환

```python
def square(x):
    return x**2

numbers = [1, 2, 3, 4, 5]
squared_numbers = map(square, numbers)
print(list(squared_numbers))  # [1, 4, 9, 16, 25]

def add(x, y):
    return x + y

numbers1 = [1, 2, 3, 4, 5]
numbers2 = [10, 20, 30, 40, 50]
added_numbers = map(add, numbers1, numbers2)
print(list(added_numbers))  # [11, 22, 33, 44, 55]
```

- max() : 최댓값 반환

max(iterable, *, key=None)<br>
max(iterable, *, default, key=None)<br>
max(arg1, arg2, *args, key=None)<br>


- memoryview(object) : 지정된 인자로부터 만들어진 메모리 뷰 객체 반환

class memoryview(object)<br>

- min() : 최솟값 반환

min(iterable, *, key=None)<br>
min(iterable, *, default, key=None)<br>
min(arg1, arg2, *args, key=None)<br>

- next() : 반복자의 메서도를 호출하여 반복자에서 다음 항목을 검색함

next(iterator)<br>
next(iterator, default)<br>

- object() : 새로운 특징 없는 객체를 반환

class object<br>

- oct(x) : 10진수를 8진수로 변환

```python
oct(8) #'0o10'
oct(-56) #'-0o70'
```

- open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None) : 파일을 열고 해당 파일 객체를 반환

- ord(c) : ascii에서 string을 숫자로 반환

```python
ord('a') #97
```

- pow(base, exp, mod=None) : base의 exp 거듭제곱을 반환

```python
pow(3, 2) #9
pow(3, 4, 2) #1
```

- print(*objects, sep='', end='\n', file=None, flush=False) : 출력 함수

```python
print("Hi", sep='', end='\n')
```

- property(fget=None, fset=None, fdel=None, doc=None) : 프로퍼티 어트리뷰트를 반환

```python
class C:
    def __init__(self):
        self._x = None

    def getx(self):
        return self._x

    def setx(self, value):
        self._x = value

    def delx(self):
        del self._x

    x = property(getx, setx, delx, "I'm the 'x' property.")


class Parrot:
    def __init__(self):
        self._voltage = 100000

    @property
    def voltage(self):
        """Get the current voltage."""
        return self._voltage

class C:
    def __init__(self):
        self._x = None

    @property
    def x(self):
        """I'm the 'x' property."""
        return self._x

    @x.setter
    def x(self, value):
        self._x = value

    @x.deleter
    def x(self):
        del self._x
```

- range() : 범위를 시퀀스 형태로 돌려줌

range(stop)<br>
range(start, stop, step=1)<br>

```python
range(10) #(0,1,2,3,4,5,6,7,8,9)
range(1, 10, step=1) #(1,2,3,4,5,6,7,8,9)
range(1, 11, step=2) #(1,3,5,7,9)
```

- repr(object) : 객체의 인쇄 가능한 표현을 포함하는 문자열을 반환

```python
class Person:
   def __init__(self, name, age):
      self.name = name
      self.age = age

   def __repr__(self):
      return f"Person('{self.name}', {self.age})"
```

- reversed(seq) : 시퀀스를 역순으로 뒤집어서 반환

- round(number, ndigits=None) : number을 소수점 다음에 ndigits 정밀도로 반올림한 값을 반환, ndigits = 0 이면 정수로 반환 

```python
round(3.14, 2) # 3.1
```

- set() : set 형식으로 반환

class set()<br>
class set(iterable)<br>

- setattr(object, name, value) : 속성 값을 정의

```python
setattr(x, 'foobar', 123) ==  x.foobar=123
```

- slice() : 인덱스 집합을 나타내는 슬라이스 객체를 반환

class slice(stop)<br>
class slice(start, stop, step=None)<br> 

- sorted(iterable, /, *, key=None, reverse=False) : 새 정렬된 리스트를 반환

- staticmethod() : 정적 메서드로 변환

```python
class C:
    @staticmethod
    def f(arg1, arg2, argN): ...

def regular_function():
...
class C:
    method = staticmethod(regular_function)
```

- str() : String타입으로 변환

class str(object='')<br>
class str(object=b'', encoding='utf-8', errors='strict')<br>

- sum(iterable, /, start=0) : 합계 반환

- super() : 부모나 형제 클래스에 위임하는 프락시 객체를 반환

class super<br>
class super(type, object_or_type=None)<br>

```python
class C(B):
    def method(self, arg):
        super().method(arg) 
```

- tuple() : 튜플 형태로 반환

class tuple<br>
class tuple(iterable)<br>

- type() : 타입 출력

class type(object)<br>
class type(name, bases, dict, **kwds)<br>

```python
a = 4
type(a) #<class : int>
```

- vars() : __dict__ 속성이 있는 모듈, 클래스, 인스턴스, 객체를 반환

- zip(*iterables, strict=False) : 여러 반복 가능한 항목을 병렬로 반복하면서 각 항목의 항목을 포함하는 튜플을 생성 반환

```python
x = [1, 2, 3]
y = [4, 5, 6]
list(zip(x, y)) #[(1, 4), (2, 5), (3, 6)]
x2, y2 = zip(*zip(x, y))
x == list(x2) and y == list(y2) #True
```

- __import__(name, globals=None, locals=None, fromlist=(), level=0) : import문에 의해 호출됨
