# Python🐍

> #### INDEX
>
> 1. [Intro](#01.-Intro)
>    1. [1. Data Type](#1-data-type)
>    2. [2. Variable & Operator](#2-variable---operator)
> 2. [Container](#02-container)
>    1. [Sequence Container](#1-sequence-container)
>    2. [Non-sequence Container](#2-non-sequence-container)
> 3. [Control flow](#03-control-flow)
>    1. [Conditional Statement](#1-conditional-statement)
>    2. [Loop Statement](#2-loop-statement)
>    3. [Cotrol Flow](#3-cotrol-flow)
> 4. [Function](#04-function)
> 5. [Error exception](#05-error-exception)
> 6. [Data Structure](#06-data-structure)
> 7. [Module](#07-module)
> 8. [OOP](#08-oop)



## 01. Intro

### 1. Data Type

> - 숫자 (Number)
> - 문자열 (String)
> - True / False (Boolean)

#### 1. 숫자 (Number)

#####  1. 정수 (`int`, Integer)

- 10진수 외에도 2진수(0b), 8진수(0o), 16진수(0x) 로도 표현 가능

  ```python
  binary_number = 0b10
  octal_number = 0o10
  decimal_number = 10
  hexadecimal_number = 0x10
  print(f"""
  2진수 : {binary_number}
  8진수 : {octal_number}
  10진수 : {decimal_number}
  16진수 : {hexadecimal_number}
  """)
  ```

- 파이썬에서 표현할 수 있는 가장 큰 수는 sys 모듈을 통해 표현 가능

  ```python
  import sys
  max_int = sys.maxsize
  # sys.maxsize 의 값은 2**63 - 1 => 64비트에서 부호비트를 뺀 63개의 최대치
  print(max_int)
  super_max = sys.maxsize * sys.maxsize
  print(super_max)
  ```



#####  2. 실수 (`float`, Floating point number)

- 컴퓨터가 표현하는 실수를 표현하는 과정에서 부동소수점을 사용

  - 비트(2진수)를 통해 숫자를 표현하는 과정에서 `floating point rounding error` 가 발생할 수 있음

- 실수의 연산과 비교 과정에서 `floating point rounding error` 를 처리하는 방법

  ```python
  x = 0.38
  y = 3.5 = 3.12
  
  # 1. math 모듈을 통해 처리 (주로 사용하는 방법)
  import math
  math.isclose(x, y)
  
  # 2. sys 모듈을 통해 처리
  # epsilon 은 부동소수점 연산에서 반올림을 함으로써 발생하는 오차 상환
  import sys
  abs(x - y) <= sys.float_info.epsilon
  
  # 3. 작은 수를 통해 처리
  abs(x - y) <= 1e-10
  ```

- `float('inf')`(양의 무한대)와 `float('-inf')`(음의 무한대)도 표현 가능

#####  3. 복소수(`complex`, Complex number)

- 실수부와 허수부를 가지며, 파이썬에서는 허수부를 `j`로 표현

- 실수부와 허수부의 값을 구하는 방법은 아래와 같음

  ```python
  z = (3+4j)
  z.real # 실수부
  z.imag # 허수부
  ```

  



#### 2. 문자열 (String)

* 문자열은 Single quotes(`'`)나 Double quotes(`"`)을 활용하여 표현 가능

  - 작은따옴표: `'"큰" 따옴표를 담을 수 있습니다'`

  - 큰따옴표: `"'작은' 따옴표를 담을 수 있습니다"`

  - 삼중 따옴표: `'''세 개의 작은따옴표'''`, `"""세 개의 큰따옴표"""`


* `PEP-8`에서는 **하나의 문장부호를 선택**하여 유지하는 것을 권장 (Pick a rule and Stick to it)



#####  1. 이스케이프 시퀀스 

- 특수문자 혹은 조작을 하기 위하여 사용되는 것으로 `\`를 활용하여 이를 구분

| 예약문자 |    내용(의미)     |
| :------: | :---------------: |
|    \n    |      줄 바꿈      |
|    \t    |        탭         |
|    \r    |    캐리지리턴     |
|    \0    |     널(Null)      |
|   \\\\   |        `\`        |
|   \\'    | 단일인용부호(`'`) |
|   \\"    | 이중인용부호(`"`) |

#####  2. String interpolation

```python
name = 'Pepper'
score = 5

# 1. f-strings (주로 사용하는 방법)
print(f'Hello, {name}. Your score is {score}!')

# 2. str.format()
print('Hello, {}. Your score is {}!'.format(name, score))

# 3. %-formating
print('Hello, %s. Your score is %d!' % (name, score))
```



#### 3. T/F (Boolean)

- `bool` 타입은 `True`와 `False`로 구성되며, 비교/논리 연산을 수행 등에서 활용

- 아래와 같이 값이 없는 것은 `False`로 변환
  - `0, 0.0, (), [], {}, '', None`
  - `None`: 값이 없음을 표현하기 위한 type



### 2. Variable & Operator

#### 1. Variable

* 변수는 `=`을 통해 할당(assignment) 

* 해당 데이터 타입을 확인하기 위해서는 `type()`을, 메모리 주소를 확인하기 위해서는 `id()`를 활용

* **식별자(Identifiers)**: 변수, 함수, 모듈, 클래스 등을 식별하는 데에 사용하는 이름

  * 식별자로 사용할 수 없는 키워드는 아래와 같음

    ```python
    import keyword
    print(keyword.kwlist)
    
    """
    ['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
    """
    ```

  * 이 외에도 `내장함수` 나 `모듈` 등의 이름도 식별자로 사용하지 않음



#### 2. Operator

#####  1. 산술 연산자

- `+` (덧셈), `-` (뺄셈), `*` (곱셈), `/` (나눗셈), `//` (몫), `%` (나머지), `**` (거듭제곱)

  - `divmod()`:  나눗셈을 통해 계산된 몫과 나머지를 한 쌍의 숫자로 반환

    - divmod(10, 3) 👉 (10  //  3, 10 % 3) 👉 (3, 1)




#####  2. 비교연산자

- 수학에서 사용하는 비교 연산자(`<`, `>` 등)와 동일
- 추가로, `==` (같음), `!=` (같지 않음), `is` (객체 아이덴티티), `is not` (부정된 객체 아이덴티티) 사용



##### 3. 논리 연산자 

| 연산자  | 내용                         |
| ------- | ---------------------------- |
| a and b | a와 b 모두 True시만 True     |
| a or b  | a 와 b 모두 False시만 False  |
| not a   | True -> False, False -> True |

- 단축평가: 첫 번째 값이 확실할 때, 두 번째 값은 확인하지 않음으로써 속도 향상
  - `and`는 a가 False이면 a를 리턴하고, True이면 b를 리턴
    - `and`는 모두 True일 경우만 True이기 때문에 a가 True일 때 b도 반드시 확인해야 함
  - `or`는 a가 True이면 a를 리턴하고, False이면 b를 리턴
    - `or`는 하나만 True여도 True이기 때문에 True를 만나면 해당 값을 반환



## 02. Container

> 여러 개의 값을 저장할 수 있는 객체
>
> - Sequence - 순서가 있는 객체
> - Non-seqeunce - 순서가 없는 객체

### 1. Sequence Container

> `Sequence`는 데이터가 순서대로 나열된 형식이며, 특정 위치 지정 가능
>
> - `list`, `tuple`, `range`, `string`, `binary` 등이 있다.

#### 1. 리스트 (`list`)

- 리스트는 `[]`, `list()`를 통해 생성

- 값에 대한 접근은 indexing, 즉 `list[idx]`를 통해 가능

- 변경가능한(mutable) 객체

  ```python
  fruits = ['apple', 'banana', 'orange']
  print(fruits[0]) 👉 'apple'
  ```

  

#### 2. 튜플 (`tuple`)

- 튜플은 `()`로 묶어서 표현

- 변경이 불가능한(immutable) 객체로, 읽을 수만 있음

  - 불변 객체이기 때문에, '값을 정확히 할당할 수 있다'는 것을 보장

- 직접 사용하기보다는 파이썬 내부에서 다양한 용도로 활용됨

  ```python
  # cf. 하나의 항목으로 구성된 튜플은 값 뒤에 쉼표를 붙여서 생성
  single_tuple = ('hello', )
  ```



#### 3. 레인지 (`range()`)

- `range`는 숫자의 시퀀스를 나타내기 위해 사용

  - `range(start, end, step)` : start부터 (end-1)까지 +step만큼 증가
    - start의 기본 값은 0, step의 기본 값은 1

  ```python
  # end 값만 입력한 기본형
  list(range(3))
   👉 [0, 1, 2]
  
  # 범위를 지정한 range
  list(range(5, 9))
   👉 [5, 6, 7, 8]
  
  # step을 활용해 다양한 배열 생성 가능
  ## 점점 작아지는 숫자 배열
  list(range(0, -5, -1))
   👉 [0, -1, -2, -3, -4]
  
  ## 1~10의 숫자 중 홀수만 담은 배열
  list(range(1, 11, 2))
   👉 [1, 3, 5, 7, 9]
  ```

  

#### + Sequence Operation

| operation      | 설명                    |
| -------------- | ----------------------- |
| x `in` s       | containment test        |
| x `not in` s   | containment test        |
| s1 `+` s2      | concatenation           |
| s `*` n        | n번만큼 반복하여 더하기 |
| `s[i]`         | indexing                |
| `s[i:j]`       | slicing                 |
| `s[i:j:k`]     | k간격으로 slicing       |
| len(s)         | 길이                    |
| min(s), max(s) | 최솟값, 최댓값          |
| s.count(x)     | x의 개수                |



### 2. Non-sequence Container

> `Non-sequence`는 데이터에 순서가 없는 형식
>
> - `set`, `dictionary` 등이 있다.



#### 1. 셋 (`set`)

- `set`은 `{}`, `set()`을 통해 생성하며, **중복된 값이 없음**

  - `set`을 활용하면 `list`의 중복된 값 제거 가능

  ```python
  # set은 집합과 동일하게 처리
  set_a = {2, 3, 5}
  set_b = {3, 6, 9}
  
  # 합집합
  print(set_a | set_b) 👉 {2, 3, 5, 6, 9}
  
  # 교집합
  print(set_a & set_b) 👉 {3}
  
  # 차집합
  print(set_a - set_b) 👉 {2, 5}
  ```

  

#### 2. 딕셔너리 (`dict`)

- `dictionary`는 `{}`, `dict()` 를 통해 생성

- 값에 대한 접근은 key (`dict[key]`)를 통해 가능

- `key`와 `value`가 쌍으로 이뤄진 궁극의 자료구조

  - `key`는 **변경 불가능(immutable)한 데이터**만 가능하며, **중복 불가능**
    - immutable : string, integer, float, boolean, tuple, range
  - `value`는 `list`, `dictionary`를 포함한 모든 것이 가능

  ```python
  # 딕셔너리 생성 방법
  dict1 = {'pepper': 5, 'kanda': 3}
  dict2 = dict(pepper=5, kanda=3)
  dict3 = dict()
  dict3['pepper'] = 5
  dict3['kanda'] = 3
  
  # 딕셔너리 메소드
  dict1.keys() 👉 dict_keys(['pepper', 'kanda'])
  dict1.values() 👉 dict_values([5, 3])
  dict1.items() 👉 dict_items([('pepper', 5), ('kanda', 3)])
  ```

  

## 03. Control flow

> **제어문**은 코드 실행의 순차적인 흐름을 제어하는 것인데, 크게 **조건문**과 **반복문**으로 분류



### 1. Conditional Statement

- `if` 조건문은 반드시 **T/F를 판단할 수 있는 조건**과 함께 사용

- `if` 조건문의 기본 구조

  - `expression`에는 일반적으로 참/거짓에 대한 조건식

  ```python
  if <expression>:
      <코드 블럭>
  else:
      <코드 블럭>
  ```

  - 조건이 True이면, `:` 이후의 문장을 수행
  - 조건이 False이면, `else:` 이후의 문장을 수행

- `elif` 로 2개 이상의 조건 활용 가능

  ```python
  if <expression>:
      <코드 블럭>
  elif <expression>:
      <코드 블럭>
  else:
      <코드 블럭>
  ```

- cf. `조건 표현식` 은 조건에 따라 값을 정할 때 활용

  ```python
  # 홀수와 짝수를 구분하는 코드를 쓴다고 할 때,
  
  num = 5
  # if 조건문의 경우,
  if num % 2:
      print('odd')
  else:
      print('even')
      
  # 조건 표현식의 경우,
  print('odd') if num % 2 else print('even')
  ```

  

### 2. Loop Statement

#### 1. `for` 반복문

- `for` 문은 시퀀스(string, tuple, list, range)나 다른 순회가능한 객체(iterable)의 요소들을 순회

- cf. `enumerate()`를 활용하면, `index`와 `value`를 함께 쓸 수 있음

  - `enumerate(iterable, start=0)`

    ```python
    students = ['Tom', 'Jerry', 'Nick', 'Sam']
    
    for idx, student in enumerate(students):
        print(idx, student)
        
    👉 0 Tom
    	1 Jerry
        2 Nick
        3 Sam
    ```

    

#### 2. `while` 반복문

- `while` 문은 조건식이 참(`True`)인 경우 반복적으로 코드를 실행

  - **반드시 종료조건을 설정**

  

#### + for 문과 while 문 비교

- [example] 1부터 N까지의 총합을 구하는 코드

  ```python
  N = 10
  
  # for 문
  total = 0
  for i in range(1, N+1):
      total += i
  print(total)
  
  # while 문
  total = 0
  i = 1
  while i <= N:
      total += i
      i += 1
  print(total)
  ```

  

### 3. Cotrol Flow

#### 1. `break`

- `break`는 반복문을 종료하고, `for` 나 `while` 문에서 빠져 탈출

- [example] animals 리스트에서 '호랑이'가 나왔을때 반복을 멈추고 '어흥!' 하는 코드

  ```python
  animals = ['고양이', '강아지', '호랑이', '고라니']
  
  for animal in animals:
      print(animal)
      if animal == '호랑이':
          print('어흥!')
          break
  ```



#### 2. `continue`

- `continue`는 `continue` 이후의 코드를 수행하지 않고, 다음 요소부터 계속 반복

- [example] students 딕셔너리에서 60점 이상인 학생만 출력하는 코드

  ```python
  students = {'Tom': 70, 'Jerry': 55, 'Nick': 47, 'Sam': 90}
  
  for student, score in students.items():
      if score < 60:
          continue
      print(f'{student}은 시험에 통과했습니다.')
  ```

- cf. `pass`는 문법적으로 문장이 필요하지만 특별히 넣을 문장이 없을 때 자리를 채우는 용도로 활용 👉 `pass`는 아무것도 하지 않음



#### 3. `for-else`

- 반복에서 리스트의 소진이나 (`for` 의 경우) 조건이 거짓이 돼서 (`while` 의 경우) 종료할 때 실행

- 반복문이 **`break` 문으로 종료될 때는 실행되지 않음

  - 즉, `break`를 통해 중간에 종료되지 않은 경우만 실행

- [example] numbers 리스트에 7이 있을 경우 `True`를, 없을 경우 `False`를 출력하는 코드

  ```python
  numbers = [1, 2, 3, 4, 5, 6]
  
  for number in numbers:
      if number == 7:
          print(True)
          break
  else:
      print(False)
  ```

  

## 04. Function

> 함수는 특정한 기능을 하는 코드의 묶음



### 1. def

* 함수 선언은 `def`로 시작하여 `:`으로 끝나고, 그 아래  `들여쓰기`로 코드 블록을 작성


* 함수는 동작후에 `return`을 통해 결과값을 전달 할 수도 있다. 


  * `return` 값이 없으면, `None`을 반환

  - ```python
    def <함수 이름>(parameter1, parameter2):
        <코드 블럭>
        return <결과 값>
    ```

- `print()` vs `return`

  - `print()` 함수는 None을 반환 👉 출력값 저장(할당) 불가
  - `return`은 값 자체를 반환



### 2. Output

- 함수의 `return` 값은 **오직 한 개의 객체**만 가능
  - `,`로 이어서 여러 개를 return하면 `tuple`로 반환
- 함수는 `return`을 만나면 종료



### 3. Input

- 매개변수(parameter)는 입력을 받아 함수 내부에서 활용할 `변수`
- 전달인자(argument)는 실제로 전달되는 `입력값` 

##### # 함수의 인자

1. 위치 인자(Positional Arguments)

   - 함수는 기본적으로 인자를 위치로 판단

   

2. 기본 인자 값(Default Argument Values)

   - 함수 호출시, 인자를 지정하지 않으면 기본 값을 대입

   - 기본 인자값을 가지는 인자 다음에는 기본 값이 없는 인자 활용 불가

     ```python
     def greeting(age, name = 'Unknown'):
         print(f'{name} is {age} years old.')
         
     greeting(5)👉 Unknown is 5 years old. 
     greeting(5, 'Pepper')👉 Pepper is 5 years old. 
     ```

   

3. 키워드 인자(Keyword Arguments)

   - 직접 변수의 이름으로 특정 인자를 전달

   - 키워드 인자를 활용한 다음에는 위치 인자 활용 불가

     ```python
     def greeting(age, name = 'Unknown'):
         print(f'{name} is {age} years old.')
     
     greeting(name = 'Pepper', age = 5)👉 Pepper is 5 years old.  
     ```

   

4. 가변 인자 리스트(Arbitrary Argument Lists)

   - 정해지지 않은 여러 개의 인자를 받기 위해 가변 인자 리스트 활용

   - 가변 인자 리스트는 tuple로 처리되며, 매개변수에 `*`로 표현

     ```python
     # 1. 가변 인자 리스트가 매개변수 목록의 마지막인 경우
     def school(prof, *students):
         print(prof)
         print(students)
         
     school('prof', 's', 't', 'u', 'd', 'e', 'n')
     
     # 2. 가변 인자 리스트가 매개변수 목록의 마지막이 아닌 경우
     ## 가변 인자 이후의 변수는 키워드 인자로 지정
     def school(*students, prof):
         print(prof)
         print(students)
         
     school('s', 't', 'u', 'd', 'e', 'n', prof = 'prof')
     ```



5. 가변 키워드 인자(Arbitrary Keyword Arguments)

   - 가변 키워드 인자들은 `dict`로 처리되며, 매개변수에 `**`로 표현

   - 주로 `kwargs`라는 이름을 사용

     ```python
     def greeting(**kwargs):
         return kwargs
     
     greeting(한국어='안녕', 영어='hi', 독일어='Guten Tag')
      👉 {'한국어': '안녕', '영어': 'hi', '독일어': 'Guten Tag'}
     ```



### 4. Scope

- 함수는 코드 내부에 공간(scope)를 생성

  - 함수로 생성된 공간은 `지역 스코프(local scope)`
  - 그 외에 코드 어디서든 참조할 수 있는 공간은 `전역 스코프(global scope)`

  ```python
  a = 10 # global
  
  def func(b):
      c = 20 # func()의 local
      print('지역스코프입니다.')
      ## local에서는 global variable 사용 가능
      print(a) # 10
      print(b) # 5
      print(c) # 20
  
  func(5)
      
  print('전역스코프입니다.')
  print(a) # 10
  ## global에서는 local variable 사용 불가
  print(b) # 에러
  print(c) # 에러
  ```



- `LEGB Rule`
  - 파이썬에서는 아래와 같은 우선순위로 이름(식별자)를 찾음
    - `L`ocal scope: 정의된 함수
    - `E`nclosed scope: 상위 함수 
    - `G`lobal scope: 함수 밖의 변수 혹은 import된 모듈
    - `B`uilt-in scope: 파이썬안에 내장되어 있는 함수 또는 속성



### 5. 재귀함수 (recursive function)

- 재귀함수는 함수 내부에서 자기 자신을 호출하는 함수

- [example] 팩토리얼 계산

  > 팩토리얼은 1부터 n 까지 양의 정수를 차례대로 곱한 값이며 `!` 기호로 표기합니다. 예를 들어 3!은 3 * 2 * 1이며 결과는 6 입니다.
  >
  > `팩토리얼(factorial)`을 계산하는 함수 `fact(n)`를 작성하세요. 
  >
  > n은 1보다 큰 정수라고 가정하고, 팩토리얼을 계산한 값을 반환합니다.

$$
\displaystyle n! = \prod_{ k = 1 }^{ n }{ k }
$$

$$
\displaystyle n! = 1*2*3*...*(n-1)*n
$$

---

```python
def factorial(n):
    # base case
    if n == 1:
        return n
    else:
        return factorial(n-1) * n
    
factorial(5)
```



## 05. Error exception

> - 에러(Error)
> - 예외 처리(Exception Handling)



### 1. Error

- [예외 계층 구조](https://docs.python.org/ko/3/library/exceptions.html#exception-hierarchy)



### 2. Exception Handling

####  1. `try-except`

- 기본 구조

  ```python
  try:
      <코드 블럭 1>
  except 예외 as err:
      <코드 블럭 2>
  else:
      <코드 블럭 3>
  finally:
      <코드 블럭 3>
  ```

  - `try` 아래의 코드 블럭 실행

    👉 예외가 발생하면 남은 부분을 수행하지 않고 `except` 실행

  - 여러 개의 `except`를 사용할 경우

    - 에러가 순차적으로 수행되기 때문에 예외 계층 구조에서 가장 작은 범주부터 예외 처리

  - `else`는 에러가 발생하지 않는 경우에 수행되는 문장

    - try 절이 예외를 일으키지 않을 때 실행되어야 하는 코드
    - `else`는 try -except 문에 의해 보호되고 있는 코드가 `일으키지 않은 예외`를 우연히 잡게 되는 것을 방지
      - ① 에러 발생의 가능성이 있는 코드나 ② 예외 처리를 원하는 코드를 try문에 넣어 예외 처리(보호)를 하고, 나머지 부분은 else문에 분리

  - `finally`는 예외의 발생 여부와 관계없이 try 문을 떠날 때 무조건 실행

    - 모든 상황에 실행되어야 하는 코드



####  2. Exception Raising

- `raise`를 활용해 예외를 강제로 발생시킬 수 있음

  ```python
  print('Start')
  raise ZeroDivisionError('division by 0!')
  print('End')
  👉 Start
     ZeroDivisionError: division by 0!
     # Error raise를 하면 그 자리에서 코드가 STOP
  ```



- (참고) `assert` 문은 상태를 검증하는 데에 사용

  - 무조건 `AssertionError`가 발생

  ```python
  assert len(['pepper', 'kanda']) == 1, '길이가 1이 아닙니다.
   👉 AssertionError: 길이가 1이 아닙니다. 
  ```

  

## 06. Data Structure

> 데이터 구조란, 데이터에 편리하게 접근하고, 변경하기 위해 데이터를 저장하거나 조작하는 방법을 말한다.
>
> - **순서가 있는(ordered)** 데이터 구조
>   - 문자열(string)
>   - 리스트(list)
> - **순서가 없는(unordered)** 데이터 구조
>   - 세트(Set)
>   - 딕셔너리(Dictionary)



### 1. String

- 변경 불가능 (immutable)
- 순서가 있고 (ordered)
- 순회 가능 (iterable)



####  1. 탐색

- `str.find(x)`

  - x의 첫 번째 위치를 반환
  - 만약, **x가 없으면 `-1`을 반환**

- `str.index(x)`

  - x의 첫 번째 위치를 반환
  - 만약, **x가 없으면 `Error`**

  ```python
  s = 'apple'
  
  s.find('a') 👉 0
  s.index('a') 👉 0
  
  s.find('f') 👉 -1
  s.index('f') 👉 Value Error
  ```

  

####  2. 변경

- `str.replace(old, new[, count])`

  - 변경할 글자(old)를 새로운 글자(new)로 바꾼 복사본을 반환
  - count를 지정하면 해당 갯수만큼만 시행

  ```python
  s  = 'zoo!gogo!'
  
  s.replace('o', '') 👉 'z!gg!'
  s.replace('o', '', 2) 👉 'z!gogo!'
  ```

  

- `str.strip([chars])`

  - 특정한 문자들을 지정하면,  양쪽 끝의 특정 문자를 제거한 복사본을 반환
    - 왼쪽을 제거 (`lstrip`), 오른쪽을 제거 (`rstrip`)
  - 지정하지 않으면 `공백 문자`를 제거



- `str.split(sep)`

  - 문자열을 특정한 단위(sep)로 나누어 리스트로 반환
  - 지정하지 않으면 `공백 문자`를 기준

  ```python
  data = '5,Tom,01012345678'
  data.split(',') 👉 ['5', 'Tom', '01012345678']
  ```

  

- `'separator'.join(iterable)`

  - separator를 구분자로 사용하여 iterable의 요소들을 이어 붙인문자열을 반환

  ```python
  words = ['Pepper', 'Kanda', 'Cell']
  '+'.join(words) 👉 'Pepper+Kanda+Cell'
  ```

  

- `str.zfill(n)`

  - 왼쪽에 `'0'`을 채워 길이가 n인 문자열의 복사본을 반환
  - n이 len(str)보다 작거나 같으면 원래 문자열을 반환

- `str.rjust(n[, fillchar])`, `str.ljust(n[, fillchar])`

  - 오른쪽(왼쪽)으로 정렬된 문자열을 지정된 fillchar를 사용하여 길이 n인 문자열로 반환 (기본값은 space)
  - n이 len(str)보다 작거나 같으면 원래 문자열을 반환

  ```python
  s = '123'
  
  s.zfill(5) 👉 '00123'
  s.rjust(5, '*') 👉 '**123'
  s.ljust(5, '*') 👉 '123**'
  ```

  

### 2. List

- 변경 가능(mutable)
- 순서가 있고(ordered)
- 순회 가능(iterable)



#### 1. 값 추가/삭제

- `list.append(x)`

  - list의 끝에 x를 추가

- `list.extend(iterable)`

  - list의 끝에 iterable의 모든 항목을 덧붙여서 확장
    - [주의] string의 개별 요소를 하나씩 다 추가

- `list.insert(idx, x)`

  - 정해진 위치 (`idx`)에 x를 추가

  ```python
  animals = ['dog']
  
  a = animals.append('cow')
  print(a) 👉 ['dog', 'cow']
  e = animals.extend(['pig', 'tiger'])
  print(e) 👉 ['dog', 'pig', 'tiger']
  i = animals.insert(1, 'cat')
  print(i) 👉 ['dog', 'cat']
      
  # 맨 끝에 insert하려면 아래와 같이 써야 함
  animals.insert(len(animals), 'end')
  animals.insert(20000, 'end')
  ```

  

- `list.remove(x)`

  - list에서 값이 x인 것을 삭제

- `list.pop(idx)`

  - 정해진 위치 idx에 있는 값을 삭제하고, 그 값을 반환
  - idx가 지정되지 않으면 **마지막 항목**을 삭제하고 반환

- `list.clear()`

  - list의 모든 항목을 삭제



#### 2. 탐색/정렬

- `list.index(x)`
  - list 내에서 x를 찾아 해당 index 값을 반환
- `list.count(x)`
  - list 내에서 x의 개수를 확인
- `list.sort()`
  - list를 정렬
  - 내장함수 `sorted()`와 달리, **원본 list를 변형**하고` None`을 리턴
- `list.reverse()`
  - list를 반대로 뒤집는다



#### 3. 복사

- 아래와 같이 list를 새로운 list에 할당해 복사를 할 경우, 

  - 두 개의 list가  같은 id를 바라보기 때문에 하나를 수정하면 두 개 다 수정

  ```python
  original_list = [1, 2, 3]
  copy_list = original_list
  copy_list[0] = '바꾼다'
  print(copy_list, original_list)
   👉 ['바꾼다', 2, 3] ['바꾼다', 2, 3]
  ```

- `shallow copy`

  - slice 연산자 사용 `[:]`

    ```python
    a = [1, 2, 3, 4]
    # 전체를 똑같이 잘라냄
    b = a[:]
    b[0] = 100
    print(a, b)
     👉 [1, 2, 3, 4]
    	[100, 2, 3, 4]
    ```

  - `list()` 활용

    ```python
    a = [1, 2, 3, 4]
    # list를 새로운 list로 형 변환
    b = list(a)
    b[0] = 100
    print(a, b)
     👉 [1, 2, 3, 4]
    	[100, 2, 3, 4]
    ```

- `deep copy`

  - 만약 중첩된 상황에서 복사를 하려면 깊은 복사를 활용
    - 내부의 모든 객체가 새롭게 값이 변경

  ```python
  import copy
  
  a = [[1, 2, 3], 2, 3]
  b = copy.deepcopy(a)
  b[0][0] = '주소'
  b[1] = '원소'
  
  print(a, b)
   👉 [[1, 2, 3], 2, 3]
      [['주소', 2, 3], '원소', 3]
  ```



#### 4. List Comprehension

- List Comprehension은 표현식과 제어문, 조건문을 통해 리스트를 생성 👉 여러 줄의 코드를 한줄로 단축 가능

  ```python
  [expression for 변수 in iterable if 조건식]
  [expression if 조건식 else 식 for 변수 in iterable]
  ```

  

- List Comprehension의 특징

  1. 간결함

  2. 성능(일반화의 오류), 최적화

     - 성능은 파이썬 자체의 변화와 코드 최적화에 따라 얼마든지 달라질 수 있다.
     - 최신 파이썬 버전은, 일반 loop문에도 비약적인 성능 향상이 있었다.
     - 물론, 일부 코드에서는 컴프리헨션이 여전히 빠르고 map보다도 빠르다
     - 다만 다른 함수나 내장함수를 적용하는 경우는 map이 더 빠름
     - 결론은, 성능이란 누가 더 빠르거나 좋다고 일반화할 수 없다.

     "List Comprehension을 남용하면 안 된다"

     - 특별한 이유없이 복잡하고 교묘하게 작성하는 것은 나쁜 기술이며 좋은 개발자라 할 수 없다
     - 중첩이 깊은 경우는 억지로 줄이는 것이 더 이해하기 어렵게 만듦
     - **코드의 가독성** >>>>> 간결함

  3. 표현력(Pythonic한 표현)



### 3. Set

- 변경 가능(mutable)
- 순서가 없고(unordered)
- 순회 가능(iterable)



- `set.add(elem)`
  - set에 elem을 추가
- `set.update(*others)`
  - set에 iterable의 모든 항목을 추가
- `set.remove(elem)`
  - set에서 elem을 삭제
  - 만약 elem이 없으면 `KeyError`
- `set.discard(elem)`
  - set에서 elem을 삭제
  - elem이 없어도 Error는 발생하지 않음
- `set.pop()`
  - set의 **임의의 원소**를 제거해 반환
  - 순서가 없은 데이터 구조는 hash table을 거쳐서 메모리에 할당되는데, 같은 구조로 계속 만들고 그래서 같은 게 계속 빠지는 것처럼 보인다 > hash table은 파이썬이 종료될 때까지 유지



### 4. Dictionary

- 변경 가능(mutable)
- 순서가 없고(unordered)
- 순회 가능(iterable)



#### 1. 조회

- `dict.get(key[,default])`
  - key를 통해 value를 반환
  - dict에 해당 key가 없어도 `KeyError`가 발생하지 않음
    - default 값을 지정할 수도 있음



#### 2. 추가 및 삭제

- `dict.pop(key[,default])`
  - dict에 key가 있으면 제거
  - key가 없으면 default를 반환 
    - default가 없으면 KeyError



- `dict.update()`

  - 값을 제공하는 key, value로 업데이트

  ```python
  my_home = {'pepper': 5, 'kanda': 3, 'cell': 27}
  
  my_home.update({'pepper': '고양이'})
  my_home.update(cell='주인')
  
  print(my_home)
   👉 {'pepper': '고양이', 'kanda': 3, 'cell': '주인'}
  ```



#### + 딕셔너리 접근 

- `dict.keys()`
- `dict.values()`
- `dict.items()`



### + Built-in Function

> 순회 가능한(iterable) 데이터 구조에 적용가능한 Built-in Function
>
> - map()
> - filter()
> - zip()
> - reduce()



- `map(function, iterable ...)`
  - iterable의 모든 요소에 function을 적용한 후 그 결과를 반환
  - return 값은 **map_object** 형태
  - custom 함수를 적용할 때 유용하게 사용



- `filter(function, iterable)`
  - iterable에서 function 반환된 결과가 True인 것들로 구성해 반환
  - return 값은 **filter_object** 형태



- `zip(*iterables)`
  - 복수의 iterable를 모아서 반환
  - return 값은 `tuple`로 구성된 **zip_object** 형태



## 07. Module

> 파일 단위의 코드 재사용 ☝
>
> - 모듈(Module)
> - 패키지(Package)



### 1. 개념 정리

1. 모듈(Module)

   - 특정 기능을 `.py` 파일 단위로 작성

2. 패키지(Package)

   - 특정 기능과 관련된 여러 모듈의 집합
   - 패키지 안에는 또 다른 서브 패키지를 포함할 수 있음

3. 파이썬 표준 라이브러리

   - PSL, Python Standard Library

   - 파이썬에 기본적으로 설치된 모듈과 내장 함수

4. 패키지 관리자(`pip`)

   - `PyPI`에 저장된 외부 패키지들을 설치하도록 도와주는 패키지



### 2. Module

- 모듈을 활용하기 위해 반드시 `import` 문을 통해 해당 스코프의 지역 이름 공간에 이름이나 이름들을 정의

  ```python
  import module
  from module import var, function, Class
  from module import *
  ```

  

- 모듈 내의 함수를 자주 사용한다면, 변수에 할당해서 사용 가능

  ```python
  import math
  
  sqrt = math.sqrt
  list(map(sqrt, range(1, 6)))
  ```

  

### 3. Package

- 패키지는 `.`(점)으로 구분된 모듈 이름(package.module)을 써서 모듈을 구조화하는 방법

- `from`과 `import` 키워드를 통해  코드를 가져와 활용

  ```python
  from package import module
  from package.module import var, function, Class
  ```

  

  - (example) 아래와 같은 패키지가 있을 때,

    ```
    my_cat/
        __init__.py
        pepper/
            __init__.py
            tools.py # func: plus, minus
        kanda/
            __init__.py
            tools.py # func: mul, div
    ```

  - 패키지 활용

    ```python
    # my_cat의 pepper 사용
    from my_cat import pepper
    
    # my_cat의 pepper의 tools 모듈 사용
    from my_cat.pepper import tools
    
    # my_cat의 pepper의 tools의 plus 함수 사용
    from my_cat.pepper.tools import plus
    ```



- `__init__.py`
  - python3.3 버전부터는 `__init__.py` 파일이 없어도 패키지로 인식
  - BUT, 하위 버전 호환 및 일부 프레임워크에서의 올바른 동작을 위해 `__init__.py` 파일을 생성하는 것을 권장

- `__name__`
  - 모듈의 이름이 저장되는 변수
  - 파이썬 인터프리터로 스크립트 파일을 **직접 실행**할 때는 모듈의 이름이 아니라 `__main__`이 들어간다
  - 해당 파일을 다른 파일에서 **import해서 사용**하면 파일 이름으로 정해진다



## 08. OOP

> - 객체 지향 프로그래밍(Object Oriented Programming)
> - 객체(Object)와 클래스(Class)



### 1. 개념정리

1. Object
   - 객체는 고유의 속성을 가지며 클래스에 정의한 행위를 수행
2. Class
   - 공통된 속성과 행위를 정의한 것으로 객체지향 프로그램의 기본적인 **사용자 정의 데이터형**
3. Instance
   - 특정 `class`로부터 생성된 해당 클래스의 실체
4. Attribute
   - 클래스나 인스턴스가 가지는 속성
5. Method
   - 클래스나 인스턴스에 적용가능한 조작법
   - 클래스나 인스턴스가 할 수 있는 행위



### 2. 객체(Object)

- Python에 존재하는 모든 것은 객체(object)
- 객체(Object)의 특징
  - **타입(type)**: 어떤 연산자(operator)와 조작(method)이 가능한가? 
  - **속성(attribute)**: 어떤 상태(데이터)를 가지는가?
  - **조작법(method)**: 어떤 행위(함수)를 할 수 있는가?



#### 1. Type & Instance

- `type`이란, 공통된 속성과 조작법을 가진 객체들의 분류
- `instance`는 특정 타입(type)의 실제 데이터 예시
  - 파이썬에서는 모든 것이 `객체`이고, 모든 객체는 `특정 타입의 인스턴스`
    - a = 1일때, a는 객체이면서 `int` 타입의 인스턴스



#### 2. Attribute & Method

- `Attribute`란, 객체의 상태/데이터

  ```python
  complex_num = 1+2j
  print(type(complex_num)) 👉 <class 'complex'>
  
  # complex 객체는 실수 속성과 허수 속성을 가짐
  print(complex_num.real, complex_num.imag) 👉 1.0 2.0
  ```

- `Method`란, 특정 객체에 적용할 수 있는 행위



### 3. Object-Oriented Programming

> OOP는 Object가 중심이 되는 프로그래밍으로, 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 개의 독립된 단위, 즉 '객체'들의 모임으로 파악하고자 하는 것이다.

- OOP의 특징

  - 코드의 **직관성**
    - 보다 직관적인 코드 분석 가능
  - 활용의 **용이성**
    - SW 개발과 보수의 간편화
  - 변경의 **유연성**
    - 프로그램의 유연화 + 변경의 용이성

- 프로그래밍의 패러다임

  ```python
  'pepper'.capitalize() #객체지향 (단축형)
   -> str.capitalize('pepper') #절차지향
  ```

  - 즉, 데이터가 흘러 다니는 것으로 보는 시각에서 데이터가 중심이 되는 시각으로 변한 것

  - 파이썬은 객체 지향 언어지만, 절차 지향 언어도 사용



### 4. Class

> - `class`란, 객체들의 분류(class)를 정의할 때 쓰이는 키워드
> - `type`이란, 공통 속성을 가진 객체들의 분류(class)



- `클래스 이름`은 `PascalCase(UpperCamelCase)` 사용

  - cf. 변수나 함수 이름은 snake_case

- 클래스 내부에는 데이터(속성)와 함수(메서드)를 정의

  ```python
  class NewClass:
      pass
  
  example = NewClass()
  print(type(example)) 
   👉 <class '__main__.NewClass'>
  print(type(NewClass))
   👉 <class 'type'>
      
  # metaclass(type)  - 재귀적으로 자기 자신을 생성
  print(type(type))
   👉 <class 'type'>
  ```

- 클래스는 `블루프린트(청사진)`이다

  - 클래스 하나로 여러 가지 인스턴스를 만드는 것
  - 각각의 인스턴스는 서로 **독립적**
    - 독자적인 이름 공간이 생기는 것



- 클래스의 기본 구조

  ```python
  class Person:
      population = 0
      
      def __init__(self, name, age):
          self.name = name
          self.age = age
          Person.population += 1
      
      def introduce(self):
          return f'안녕하세요! {self.age} 살, {self.name} 입니다.'
      
      @classmethod
      def get_population(cls):
          return f'현재 인구는 {cls.population} 입니다.'
      
      @staticmethod
      def info():
          return 'Person class를 만들고 있습니다.'
      
      def __del__(self):
          Person.population -= 1
  ```

  

- `매직메서드`

  - 더블 언더스코어(`__`)가 있는 메서드로, 특별한 일을 하기 위해 만들어진 메서드
    - `__init__` : 인스턴스 객체가 생성될 때 호출되는 함수
    - `__del__` : 인스턴스 객체가 소멸되기 직전에 호출되는 함수
    - `__str__` : 특정 객체를 출력(`print()`)할 때 보여줄 내용을 정의하는 함수
    - 이 외에도 다양한 매직메서드가 존재



- 메서드의 종류는 `instance method`, `class method`, `static method`
  - 인스턴스는 3가지 메서드 모두에 접근 가능
    - BUT 인스턴스에서 클래스 메서드와 스태틱 메서드 호출하지 말기
    - 인스턴스가 할 행동은 모두 인스턴스 메서드로 한정 지어서 설계
  - 클래스 또한 3가지 메서드 모두에 접근 가능
    - BUT 클래스에서 인스턴스 메서드는 호출하지 말기
    - 클래스가 할 행동은 다음 원칙에 따라 설계
      - 클래스 자체(`cls`)와 그 속성에 접근할 필요가 있다면 **클래스 메서드**로 정의
      - 클래스와 클래스 속성에 접근할 필요가 없다면 **정적 메서드**로 정의
        - 정적 메서드는 `cls`, `self`와 같이 묵시적인 첫번째 인자를 받지 않기 때문



### 5. 상속

- 클래스는 `상속`이 가능

  - 부모 클래스의 모든 속성이 자식 클래스에게 상속되어 재사용성 ☝

  ```python
  class Person:
      population = 0
      
      def __init__(self, name='Unknown'):
          self.name = name
          Person.population += 1
          
      def greeting(self):
          print(f'Hi! My name is {self.name}.')
    
  
  class Student(Person):
      def __init__(self, name, student_id):
          super().__init__(name)
          self.student_id = student_id
  ```



- 클래스와 상속관계에서의 `이름 공간`
  - 인스턴스 👉 자식 클래스 👉 부모 클래스 👉 전역 순으로 이름 공간을 탐색
  - `class.mro()` : 메서드를 가져오는 순서



- `다중 상속` 도 가능

  ```python
  class Person:
      def __init__(self, name):
          self.name = name
      def info(self):
          print('사람입니다.')
          
  class Mom(Person):
      gene = 'XX'
      def talk(self):
          print('엄마 왔다!!!!')
          
  class Dad(Person):
      gene = 'XY'
      def sing(self):
          print('아빠 곰은 뚱뚱해')
          
  class Girl(Mom, Dad):
      def sing(self):
          print('아기 곰은 너무 귀여워')
          
  class Boy(Dad, Mom):
      def cry(self):
          print('으앙')
          
  first_baby = Girl('Tommy')
  second_baby = Boy('Jerry')
  
  # 상속 받을 class을 정의하는 순서에 따라 이름 공간 탐색 순서가 변동
  print(first_baby.gene) 👉 'XX'
  print(second_baby.gene) 👉 'XY'
  ```

  

