# JavaScript🔥

> ## INDEX
>
> 1. [Variable](#1.-Variable)
>    1. [식별자 (Identifier)](#1.-식별자 (Identifier))
>    2. [변수 선언](#2.-변수-선언)
> 2. [Data Type](#2.-Data-Type)
> 3. [Control flow](#3.-Control-flow)
>    1. [Conditions](#1.-Conditions)
>    2. [Loops](#2.-Loops)
> 4. [Function](#4.-Function)
> 5. [Object](#5-arrays--objects)
>
> - [[참고] `this` in JavaScript](#-this-in-javascript)



## 1. Variable

> - 자바스크립트에서 변수를 선언하는 키워드
>
>   | 키워드  | 재선언 | 재할당 | 스코프 |   etc.   |
>   | :-----: | :----: | :----: | :----: | :------: |
>   |  `let`  |   X    |   O    |  블록  | ES6 도입 |
>   | `const` |   X    |   X    |  블록  | ES6 도입 |
>   |  `var`  |   O    |   O    |  함수  |  권장 X  |



### 1. 식별자 (Identifier)

> - 변수를 구분할 수 있는 변수명
> - 반드시 문자, `$`, `_`로 시작해야 하며, 클래스명 외에는 모두 소문자로 시작



####  🚩 식별자 작성 스타일

1. 카멜 케이스(`camelCase`, lower-camel-case)

   - 변수, 객체, 함수에 사용

     ```javascript
     // [example]
     let variableName
     const userInfo = { name: 'pepper', age: 5 }
     function getUserName () {}
     ```

2. 파스칼 케이스(`PascalCase`, upper-camel-case)

   - 클래스, 생성자에 사용

     ```javascript
     // [example]
     class User {
       constructor(options) {
         this.name = options.name
       }
     }
     const person = new user({
       name: 'Pepper'
     })
     ```

     

3. 대문자 스네이크 케이스(`SNAKE_CASE`)

   - 상수(개발자의 의도와 상관없이 변경될 가능성이 없는 값)에 사용

     ```javascript
     // [example]
     const API_KEY = 'adslhalf-wrljr21'
     const PI = Math.PI
     ```



### 2. 변수 선언

#### 1. 기본 개념

1. 선언(Declaration)
   - 변수를 생성하는 행위 또는 시점
2. 할당(Assignment)
   - 선언된 변수에 값을 저장하는 행위 또는 시점
3. 초기화(Intialization)
   - 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점



#### 2. 변수 선언 키워드

| `let`                                                        | `const`                                                      | `var`                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| - 변수 재할당 가능<br />- 변수 재선언 불가능<br />- 블록 스코프 | - 변수 재할당 불가능<br />- 변수 재선언 불가능<br />- 블록 스코프 | - 변수 재할당 가능<br />- 변수 재선언 가능<br />- 함수 스코프 |

- `let` vs `const`

  ```javascript
  // 1. 차이점 👉 재할당
    // 1) let - 재할당 가능
    let number = 1
    number = 2
    console.log(number) // → 2
  
    // 2) const - 재할당 불가능
    const number = 1
    number = 2 // → Uncaught TypeError
  
  // 2. 공통점
  	// 1) 재선언 불가능 
    let number = 1
    let number = 2 // → Uncaught SyntaxError
    const number = 1
    const number = 2 // → Uncaught SyntaxError
    
    // 2) 블록 스코프
    let name = 'Pepper'
    if (name === 'Pepper') {
      let name = 'Kanda'
      console.log('블록 스코프:', name) // 블록 스코프: Kanda
    }
    console.log('전역 스코프:', name) // 전역 스코프: Pepper
  
    const name = 'Pepper'
    if (name === 'Pepper') {
      const name = 'Kanda'
      console.log('블록 스코프:', name) // 블록 스코프: Kanda
    }
    console.log('전역 스코프:', name) // 전역 스코프: Pepper
  ```



- `var`

  - **호이스팅**되는 특성으로 인해 예기치 못한 문제 발생 가능

    - 변수를 선언 이전에 참조할 수 있는 현상으로, 선언 이전의 위치에서 접근 시 `undefined` 반환

      ```javascript
      console.log(name) // undefined
      var name = 'Pepper'
      
      // 선언 이전에 접근하면, 아래와 같은 방식으로 인식
      var name // → 선언문이 위로 끌어올려지는 것
      console.log(name) // undefined
      name = 'Pepper'
      ```



## 2. Data Type

>- 자바스크립트의 모든 값은 특정한 데이터 타입을 가지는데,
>
> - 크게 원시 타입(Primitive type)과 참조 타입(Reference type)으로 분류
>
>   1. 원시 타입
>
>      - Number, String, Boolean, undefined, null, Symbol
>
>   2. 참조 타입 👉 Objects
>
>      - 객체(Objects) 타입의 자료형
>        - 변수에 해당 객체의 참조 값이 담기고, 참조 값을 복사
>
>      - Array, Function, Object, ...



### 1. Primitive Type

> - 객체(Objects)가 아닌 기본 타입
>
> - 변수에 해당 타입의 값이 담기고, 실제 값을 복사



#### 1. Number

- 정수, 실수 구분이 없는 하나의 숫자 타입
  - 부동소수점 형식
  - cf. `NaN`(Not-A-Number)
    - 계산 불가능한 경우 반환되는 값



#### 2. String

- 텍스트 데이터를 나타내는 타입

  - 16비트 유니코드 문자의 집합

- 템플릿 리터럴 (Template Literal)

  - backtick(`) 으로 표현

  - `${ expression } 형태로 표현식 삽입

    ```javascript
    const name = 'Pepper'
    const age = 5
    const introduce = `${name} is ${age} years old.`
    ```



#### 3. undefined & null

| undefined                                                    | null                                               |
| ------------------------------------------------------------ | -------------------------------------------------- |
| 빈 값을 표현하기 위한 데이터 타입                            | 빈 값을 표현하기 위한 데이터 타입                  |
| 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 `undefined`가 할당 | 개발자가 빈 값을 표현하기 위해 **의도적으로 **할당 |
| `typeof undefined` 결과 값은 `undefined`                     | `typeof null` 결과 값은 객체(`object`)             |



#### 4. Boolean

- 논리적 참/거짓을 나타내는 타입

  - true/false로 표현

- 조건문 또는 반복문에서 유용하게 사용

  - cf. 자동 형변환 규칙

    |  Data Type  |    true     |   false    |
    | :---------: | :---------: | :--------: |
    | `undefined` |      -      | 항상 거짓  |
    |   `null`    |      -      | 항상 거짓  |
    |   Number    | 나머지 경우 | 0, -0, NaN |
    |   String    | 나머지 경우 | 빈 문자열  |
    |   Object    |   항상 참   |     -      |

    

### 2. 연산자

#### 1. 할당 연산자

- 다양한 연산에 대한 단축 연산자 지원

  ```javascript
  // 1. 기본 할당
  let x = 0
  
  // 2. 사칙연산
  x += 1
  x -= 2
  x *= 3
  x /= 4
  
  // 3. Increment & Decrement 연산자
  x++ // += 1 과 동일
  x-- // -= 1 과 동일
  ```

  

#### 2. 비교 연산자

- 피연산자(숫자, 문자, Boolean 등)를 비교하고 비교의 결과값을 Boolean으로 반환하는 연산자
- 문자열은 유니코드 값을 사용하며 표준 사전순서를 기반으로 비교
  - 알파벳끼리 비교할 경우
    - 알파벳 오름차순으로 우선순위를 지님
    - 소문자가 대문자보다 우선순위를 지님



#### 3. 동등 비교 연산자 (`==`)

- 두 피연산자가 같은 값으로 평가되는지 비교 후 Boolean 값 반환
  - **암묵적 타입 변환**을 통해 타입을 일치시킨 후 같은 값인지 비교
    - 예상치 못한 결과가 발생할 수 있으므로 특별한 경우를 제외하고 사용하지 않음
  - 두 피연산자가 모두 객체일 경우, 메모리의 같은 객체를 바라보는지 판별



#### 4. 일치 비교 연산자 (`===`)

- 두 피연산자가 ① 같은 타입인지 확인하고 ② 같은 값으로 평가되는지 비교 후 Boolean 값 반환
  - **엄격한 비교**가 이뤄지며 암묵적 타입 변환이 발생하지 않음
  - 두 피연산자가 모두 객체일 경우, 메모리의 같은 객체를 바라보는지 판별



#### 5. 논리 연산자

- 세 가지 논리 연산자로 구성
  - and 연산은 `&&` 연산자
  - or 연산은 `||` 연산자
  - not 연산은 `!` 연산자



#### 6. 삼항 연산자

- 세 개의 피연산자를 사용하여 조건에 따라 값을 반환하는 연산자

  - `condition ? optionA : optionB`

    - 조건식이 참이면 A 값을, 거짓이면 B 값을 사용

  - 삼항 연산자의 결과는 변수에 할당 가능

  - 한 줄에 표기하는 것을 권장

    ```javascript
    console.log(true ? 1 : 2) // → 1
    console.log(false ? 1 : 2) // → 2
    ```

    

## 3. Control flow

### 1. Conditions

#### 1. if statement

- 조건 표현식의 결과값을 Boolean 타입으로 변환 후 참/거짓 판단

  ```javascript
  if (condition) {
      // do something
  } else if (condition) {
      // do something
  } else {
      // do something
  }
  ```



#### 2. switch statement

- 조건 표현식의 결과 값이 어느 값(case)에 해당하는지 판별

  - 주로 특정 변수의 값에 따라 조건을 분기할 때 활용
    - 조건이 많아질 경우, if문보다 가독성이 나을 수 있음

  ```javascript
  switch(expression) {
      case 'first value': {
        // do something
        break
      }
      case 'second value': {
        // do something
        break
      }
      default : {
        // do something
      }
  }
  ```

  - `break`, `default` 문은 선택적으로 사용 가능
    - break문이 없는 경우,  break문을 만나거나 default문을 실행할 때까지 다음 조건문 실행



#### cf. `if` vs `switch`

```javascript
const numOne = 100
const numTwo = 7
let operator = '+'

// 1. if statement
if (operator == '+') {
  console.log(numOne + numTwo)
} else if (operator == '-') {
  console.log(numOne - numTwo)
} else if (operator == '*') {
  console.log(numOne * numTwo)
} else if (operator == '/') {
  console.log(numOne / numTwo)
} else {
  console.log('올바른 연산자를 입력해주세요.')
}

// 2. switch statement
switch(operator) {
  case '+': {
    console.log(numOne + numTwo)
    break
  }
  case '-': {
    console.log(numOne - numTwo)
    break
  }
  case '*': {
    console.log(numOne * numTwo)
    break
  }
  case '/': {
    console.log(numOne / numTwo)
    break
  }
  default: {
    console.log('올바른 연산자를 입력해주세요.')
  }
}
```



### 2. Loops

#### 1. while

- 조건문이 참인 동안 반복 시행

  ```javascript
  let num = 0
  
  while (num < 10) {
    console.log(num)
    num += 1
  }
  ```

  

#### 2. for

- 세미콜론 `;` 으로 구분되는 세 부분으로 구성

  - initialization : 최초 반복문 진입 시 1회만 실행

  - condition : 매 반복 시행 전 평가되는 부분

  - expression : 매 반복 시행 이후 평가되는 부분

    ```javascript
    for (initialization; condition; expression) {
      // do something
    }
    ```

  ```javascript
  for (let num = 0; num < 10; num++) {
    console.log(num)
  }
  ```



#### 3. for - in

- 객체(object)의 속성들을 순회할 때 사용

  - 배열 순회도 가능하나 권장하지 않음

  ```javascript
  const animals = {
      Pepper: 'tiger',
      Kanda: 'cat',
      Tony: 'dog'
  }
  
  for (let animal in animals) {
      console.log(animal)
  }
  ```

  

#### 4. for - of

- 반복 가능한(iterable) 객체를 순회하며 값을 꺼낼 때 사용

  ```javascript
  const animals = ['Pepper', 'Kanda', 'Tony']
  
  for (let animal of animals) {
      console.log(animal)
  }
  ```

  

## 4. Function

> - 자바스크립트 함수는 일급 객체(First-class citizens)
>   - 변수에 할당 가능
>   - 함수의 매개변수로 전달 가능
>   - 함수의 반환 값으로 사용 가능



### 1. 함수 선언식

- 함수의 이름과 함께 정의하는 방식

  - 익명 함수 불가능, 호이스팅 O

  ```javascript
  function name (args) {
      // do something 
  }
  ```

  

### 2. 함수 표현식

- 힘수를 표현식 내에서 정의하는 방식

  - 함수 이름을 생략하고 익명 함수로 정의 가능, 호이스팅 X
  - Airbnb Style Guide 권장 방식

  ```javascript
  const myFunction = function (args) {
      // do something
  }
  ```

  

#### cf. 함수 선언식 vs 함수 표현식

1. 호이스팅

   ```javascript
   // 1. 함수 선언식 👉 호이스팅 O
   
   plus(2, 5) // → 7
   
   function plus (num1, num2) {
       return num1 + num2
   }
   
   // 2. 함수 표현식 👉 호이스팅 X
   minus(5, 2) // → Uncaught ReferenceError
   
   const minus = function (num1, num2) {
       return num1 - num2
   }
   ```

   

### 3. 화살표 함수 (Arrow Function)

- 함수를 비교적 간결하게 정의할 수 있는 문법

  1. function 키워드 생략 가능

  2. 함수의 **매개변수가 하나** 뿐이면 `()`도 생략 가능
  3. 함수 바디에 표현식 하나라면 `{}`과 `return` 생략 가능

- [example]

  ```javascript
  // 0. 함수 표현식
  const greeting = function (name) {
      return `hello, ${name}`
  }
  
  // 1. function 생략
  const greeting = (name) => { return `hello, ${name}` }
  
  // 2. () 생략
  const greeting = name => { return `hello, ${name}` }
  
  // 3. {} & return 생략
  const greeting = name => `hello, ${name}`
  ```

  

## 5. Arrays & Objects

### 1. Arrays

> 키와 속성들을 담고 있는 참조 타입의 객체(object)
>
> - 순서 보장
> - 0을 포함한 양의 정수 인덱스로 특정 값에 접근
> - 배열의 길이는 `array.length`로 접근



#### 1. 기본 배열 조작 Method

| Method          | Description                                          | etc.                    |
| --------------- | ---------------------------------------------------- | ----------------------- |
| reverse         | 원본 배열의 요소들의 순서를 반대로 정렬              |                         |
| push & pop      | 배열의 가장 뒤에 요소를 추가 또는 제거               |                         |
| unshift & shift | 배열의 가장 앞에 요소를 추가 또는 제거               |                         |
| includes        | 배열에 특정 값이 존재하는지 판별 후 참/거짓 반환     |                         |
| indexOf         | 배열에 특정 값이 존재하는지 판별 후 해당 인덱스 반환 | 없을 경우 -1 반환       |
| join            | 배열의 모든 요소를 구분자를 매개로 연결              | 구분자 생략 시 쉼표 `,` |
| splice          | 배열에 요소를 추가・삭제・교체                       |                         |

```js
// splice(특정 지점 idx, 삭제할 갯수[, 추가할 요소])
const months = ['Jan', 'Mar', 'Apr', 'Jun']

months.splice(1, 0, 'Feb')
console.log(months) // ['Jan', 'Feb', 'Mar', 'Apr', 'Jun']

months.splice(4, 1, 'May')
console.log(months) // ['Jan', 'Feb', 'Mar', 'Apr', 'May']
```



#### 2. Array Helper Methods

- 배열을 순회하며 특정 로직을 수행하는 메서드
- 메서드 호출 시 인자로 callback 함수를 받는 것이 특징
  - callback 함수: 어떤 함수의 내부에서 실행될 목적으로 인자로 넘겨받는 함수

| Method  | Description                                                  |
| ------- | ------------------------------------------------------------ |
| forEach | 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행 (반환 값 없음) |
| map     | 콜백 함수의 반환 값을 요소로 하는 새로운 배열 반환           |
| filter  | 콜백 함수의 반환 값이 `true`인 요소들만 모아 새로운 배열 반환 |
| reduce  | 콜백 함수의 반환 값들을 하나의 값(acc)에 누적 후 반환        |
| find    | 콜백 함수의 반환 값이 `true`면 해당 요소를 반환              |
| some    | 배열의 요소 중 **하나**라도 판별 함수를 통과하면 `true`를 반환 |
| every   | 배열의 **모든 요소**가 판별 함수를 통과하면 `true`를 반환    |

- `array.forEach(callback(element[, index[, array]]))`

  - break, continue 사용 불가능

  ```javascript
  const students = ['Tim', 'Harry', 'Jackson', 'carol']
  
  students.forEach((name, index) => {
      console.log(name, index)
  })
  ```

  

- `array.map(callback(element[, index[, array]]))`

- `array.filter(callback(element[, index[, array]]))`

  ```javascript
  const nums = [1, 2, 3, 4, 5]
  
  const doulbleNums = nums.map((num) => {
      return num * 2
  })
  
  const oddNums = nums.filter((num) => {
      return num % 2
  })
  
  console.log(doulbleNums) // 👉 [2, 4, 6, 8, 10]
  console.log(oddNums) // 👉 [1, 3, 5]
  ```



- `array.reduce(callback(acc, element, [index[, array]])[, initialValue])`

  - `acc` : 이전 callback 함수의 반환 값이 누적되는 변수
  - `initialValue` : callback 함수 최초 호출 시, acc에 할당되는 값
    - 설정하지 않으면 배열의 첫 번째 값으로 사용

  ```javascript
  const nums = [1, 2, 3, 4, 5]
  
  const sumOfNums = nums.reduce((acc, num) => {
      return acc + num
  }, 0)
  
  console.log(sumOfNums) // 👉 15
  ```

  

- `array.find(callback(element[, index[, array]]))`

  - 찾는 값이 배열에 없으면 `undefined` 반환

  ```javascript
  const students = [
      { name: 'Tim', score: 87}, 
      { name: 'Harry', score: 92},
      { name: 'Jackson', score: 76},
      { name: 'Carol', score: 100},
  ]
  
  const result = students.find((student) => {
      return student.score == 100
  })
  
  console.log(result) // 👉 { name: 'Carol', score: 100}
  ```

  

- `array.some(callback(element[, index[, array]]))`

  - 빈 배열은 항상 `false`

- `array.every(callback(element[, index[, array]]))`

  - 빈 배열은 항상 `true`

  ```javascript
  const nums = [1, 2, 3, 4, 5]
  
  const hasOddNum = nums.some((num) => {
      return num % 2
  })
  
  const isEveryNumsOdd = nums.every((num) => {
      return num % 2
  })
  ```

  

#### 3. 배열 순회 방식

```javascript
const animals = ['Cat', 'Dog', 'Lion', 'Tiger', 'Snake', 'Bird']

// 1. for loop (break문 사용 가능)
for (let i = 0; i < animals.length; i++) {
    console.log(i, animals[i])
}

// 2. for - of
for (animal of animals) {
    console.log(animal)
}

// 3. forEach (break문 사용 불가능)
animals.forEach((animal, index) => {
    console.log(index, animal)
})
```



### 2. Objects

> 속성의 집합으로, 중괄호 내부에 key-value 쌍으로 표현 
>
> - key는 문자열 타입 (구분자가 있을 경우 따옴표로 묶어서 표현)
> - value는 모든 타입



 #### 1. 객체 생성 및 조작 문법

1. 속성명 축약

   - 객체 정의 시, key와 할당하는 변수 이름이 같으면 축약 가능

     ```javascript
     let fruits = ['apple', 'orange', 'banana', 'lemon']
     let vagetables = ['mushroom']
     
     const market = {
         fruits,
         vegetables,
     }
     ```

     

2. 메서드명 축약

   - 메서드 선언시 function 키워드 생략 가능

     ```javascript
     const greeting = {
         hello() {
             console.log('Hello!')
         }
     }
     ```

     

3. 계산된 속성 사용

   - 객체 정의 시 key 이름을 표현식을 통해 동적으로 생성 가능

     ```javascript
     const firstCat = 'pepper'
     const secondCat = 'kanda'
     const myCats = {
         [firstCat]: 5,
         [secondCat.toUpperCase()]: 3,
     }
     
     console.log(myCats) // 👉 {pepper: 5, KANDA: 3}
     ```

     

4. 구조 분해 할당

   - 배열 또는 객체를 분해하여 속성을 변수에 쉽게 할당할 수 있는 문법

     - key와 변수 명이 같을 경우 사용 가능

     ```javascript
     const info = {
         name: 'Pepper',
         age: 5, 
         color: 'Grey'
     }
     
     const { name } = info
     const { age, color } = info
     ```



### 3. JSON

> JavaScript Object Notation
>
> - key-value 쌍 형태의 데이터를 표기하는 언어 독립적 표준 포맷
>   - 자바스크립트 객체(objects)와 유사하게 생겼으나, 실제로는 **문자열 타입**
> - JSON을 조작하기 위한 두 가지 내장 메서드
>   - `JSON.parse()` 👉 JSON > 자바스크립트 객체
>   - `JSON.stringify()` 👉 자바스크입트 객체 > JSON





## * `this` in JavaScript

> 함수 호출 방식에 의해 결정되는 `this`
>
> - 자바스크립트는 해당 함수 호출 방식에 따라 this에 바인딩되는 객체가 달라짐
> - 즉, 함수를 선언할 때 this의 객체가 결정되는 게 아니라, **함수를 어떻게 호출하는지에 따라 동적으로 결정**되는 것



### 1. 함수 호출 방식

#### 1. 함수 호출

> 전역 객체는 모든 객체의 유일한 최상위 객체를 의미하며, 일반적으로 Browser에서는 `window`

```js
const checkThis = function () {
    console.log(this)
}

checkThis() // 👉 window
```

- 기본적인 함수 선언을 하고, 전역에서 호출할 경우 전역 객체가 바인딩



#### 2. 메서드 호출

```js
const user = {
    name: 'pepper',
    checkThis,
}

user.checkThis() // 👉 {name: "pepper", checkThis: ƒ}
```

- 메서드로 선언하고 호출할 경우, 객체의 메서드이므로 해당 객체가 바인딩



#### 3. Arrow Function

> - 화살표 함수는 호출 위치와 상관없이 상위 스코프를 가리킴
>   - Lexical scope
>     - 함수를 어디서 호출하는지가 아니라 **어디에 선언**하였는지에 따라 결정

```js
const checkArrowThis = () => {
    console.log(this)
}

const user = {
    name: 'kanda',
    checkArrowThis,
}

checkArrowThis() // 👉 window
user.checkArrowThis() // 👉 window
```

- 메서드 선언을 화살표 함수로 하면, 해당 객체의 상위 스코프인 전역 객체가 바인딩

  - checkArrowThis() 함수가 애초에 전역에서 선언되었기 때문

    👉 **메서드 선언은 function 키워드**를 통해 정의해야 함



### 2. ES6에서의 화살표 함수

#### 1. 함수 내 함수

- function 키워드

  ```js
  const zoo = {
      animals: ['Lion'],
      print: function () {
          console.log(this) // {animals: Array(1), print: ƒ}
          console.log(this.animals) // ["Lion"]
          this.animals.forEach(function (animal) {
              console.log(animal) // Lion
              console.log(this) // window
          })
      }
  }
  
  zoo.print()
  ```

  - 전역에서 호출되었기 때문에 forEach의 콜백 함수에서 this에는 전역 객체인 window 바인딩

  

- 화살표 함수

  ```js
  const zoo = {
      animals: ['Lion'],
      print: function () {
          console.log(this) // {animals: Array(1), print: ƒ}
          console.log(this.animals) // ["Lion"]
          this.animals.forEach((animal) => {
              console.log(animal) // Lion
              console.log(this) // {animals: Array(1), print: ƒ}
          })
      }
  }
  
  zoo.print()
  ```

  - print 메서드 내에 forEach의 콜백함수에서의 상위 스코프는 zoo 객체

    - 호출 위치와 관계 없이 선언 위치의 상위 스코프를 가리키는 화살표 함수는 this에 zoo가 바인딩

      👉 **함수 내의 함수 상황에서는 화살표 함수**를 쓰는 것이 좋음



#### 2. 이벤트 리스너

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <button id="function">function</button>
  <button id="arrow">arrow function</button>
  <script>
    const functionButton = document.querySelector('#function')
    const arrowButton = document.querySelector('#arrow')
    
    functionButton.addEventListener('click', function(event) {
      console.log(this) // <button id="function">function</button>
    })
    arrowButton.addEventListener('click', event => {
      console.log(this) // window
    })
  </script>
</body>
</html>
```

- addEventListener에서의 콜백 함수는,

  - 특별하게 function 키워드의 경우에 이벤트 리스너를 호출한 대상을( event.target ) 뜻함

    👉 따라서, 호출한 대상을 원한다면 this 를 활용할 수 있음

  - 다만, 화살표 함수의 경우 상위 스코프를 지칭하기 때문에 window 객체가 바인딩 됨

- **이벤트 리스너의 콜백 함수는 function 키워드**를 사용