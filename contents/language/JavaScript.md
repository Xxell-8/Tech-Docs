# JavaScriptπ₯

> ## INDEX
>
> 1. [Variable](#1.-Variable)
>    1. [μλ³μ (Identifier)](#1.-μλ³μ (Identifier))
>    2. [λ³μ μ μΈ](#2.-λ³μ-μ μΈ)
> 2. [Data Type](#2.-Data-Type)
> 3. [Control flow](#3.-Control-flow)
>    1. [Conditions](#1.-Conditions)
>    2. [Loops](#2.-Loops)
> 4. [Function](#4.-Function)
> 5. [Object](#5-arrays--objects)
>
> - [[μ°Έκ³ ] `this` in JavaScript](#-this-in-javascript)



## 1. Variable

> - μλ°μ€ν¬λ¦½νΈμμ λ³μλ₯Ό μ μΈνλ ν€μλ
>
>   | ν€μλ  | μ¬μ μΈ | μ¬ν λΉ | μ€μ½ν |   etc.   |
>   | :-----: | :----: | :----: | :----: | :------: |
>   |  `let`  |   X    |   O    |  λΈλ‘  | ES6 λμ |
>   | `const` |   X    |   X    |  λΈλ‘  | ES6 λμ |
>   |  `var`  |   O    |   O    |  ν¨μ  |  κΆμ₯ X  |



### 1. μλ³μ (Identifier)

> - λ³μλ₯Ό κ΅¬λΆν  μ μλ λ³μλͺ
> - λ°λμ λ¬Έμ, `$`, `_`λ‘ μμν΄μΌ νλ©°, ν΄λμ€λͺ μΈμλ λͺ¨λ μλ¬Έμλ‘ μμ



####  π© μλ³μ μμ± μ€νμΌ

1. μΉ΄λ© μΌμ΄μ€(`camelCase`, lower-camel-case)

   - λ³μ, κ°μ²΄, ν¨μμ μ¬μ©

     ```javascript
     // [example]
     let variableName
     const userInfo = { name: 'pepper', age: 5 }
     function getUserName () {}
     ```

2. νμ€μΉΌ μΌμ΄μ€(`PascalCase`, upper-camel-case)

   - ν΄λμ€, μμ±μμ μ¬μ©

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

     

3. λλ¬Έμ μ€λ€μ΄ν¬ μΌμ΄μ€(`SNAKE_CASE`)

   - μμ(κ°λ°μμ μλμ μκ΄μμ΄ λ³κ²½λ  κ°λ₯μ±μ΄ μλ κ°)μ μ¬μ©

     ```javascript
     // [example]
     const API_KEY = 'adslhalf-wrljr21'
     const PI = Math.PI
     ```



### 2. λ³μ μ μΈ

#### 1. κΈ°λ³Έ κ°λ

1. μ μΈ(Declaration)
   - λ³μλ₯Ό μμ±νλ νμ λλ μμ 
2. ν λΉ(Assignment)
   - μ μΈλ λ³μμ κ°μ μ μ₯νλ νμ λλ μμ 
3. μ΄κΈ°ν(Intialization)
   - μ μΈλ λ³μμ μ²μμΌλ‘ κ°μ μ μ₯νλ νμ λλ μμ 



#### 2. λ³μ μ μΈ ν€μλ

| `let`                                                        | `const`                                                      | `var`                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| - λ³μ μ¬ν λΉ κ°λ₯<br />- λ³μ μ¬μ μΈ λΆκ°λ₯<br />- λΈλ‘ μ€μ½ν | - λ³μ μ¬ν λΉ λΆκ°λ₯<br />- λ³μ μ¬μ μΈ λΆκ°λ₯<br />- λΈλ‘ μ€μ½ν | - λ³μ μ¬ν λΉ κ°λ₯<br />- λ³μ μ¬μ μΈ κ°λ₯<br />- ν¨μ μ€μ½ν |

- `let` vs `const`

  ```javascript
  // 1. μ°¨μ΄μ  π μ¬ν λΉ
    // 1) let - μ¬ν λΉ κ°λ₯
    let number = 1
    number = 2
    console.log(number) // β 2
  
    // 2) const - μ¬ν λΉ λΆκ°λ₯
    const number = 1
    number = 2 // β Uncaught TypeError
  
  // 2. κ³΅ν΅μ 
  	// 1) μ¬μ μΈ λΆκ°λ₯ 
    let number = 1
    let number = 2 // β Uncaught SyntaxError
    const number = 1
    const number = 2 // β Uncaught SyntaxError
    
    // 2) λΈλ‘ μ€μ½ν
    let name = 'Pepper'
    if (name === 'Pepper') {
      let name = 'Kanda'
      console.log('λΈλ‘ μ€μ½ν:', name) // λΈλ‘ μ€μ½ν: Kanda
    }
    console.log('μ μ­ μ€μ½ν:', name) // μ μ­ μ€μ½ν: Pepper
  
    const name = 'Pepper'
    if (name === 'Pepper') {
      const name = 'Kanda'
      console.log('λΈλ‘ μ€μ½ν:', name) // λΈλ‘ μ€μ½ν: Kanda
    }
    console.log('μ μ­ μ€μ½ν:', name) // μ μ­ μ€μ½ν: Pepper
  ```



- `var`

  - **νΈμ΄μ€ν**λλ νΉμ±μΌλ‘ μΈν΄ μκΈ°μΉ λͺ»ν λ¬Έμ  λ°μ κ°λ₯

    - λ³μλ₯Ό μ μΈ μ΄μ μ μ°Έμ‘°ν  μ μλ νμμΌλ‘, μ μΈ μ΄μ μ μμΉμμ μ κ·Ό μ `undefined` λ°ν

      ```javascript
      console.log(name) // undefined
      var name = 'Pepper'
      
      // μ μΈ μ΄μ μ μ κ·Όνλ©΄, μλμ κ°μ λ°©μμΌλ‘ μΈμ
      var name // β μ μΈλ¬Έμ΄ μλ‘ λμ΄μ¬λ €μ§λ κ²
      console.log(name) // undefined
      name = 'Pepper'
      ```



## 2. Data Type

>- μλ°μ€ν¬λ¦½νΈμ λͺ¨λ  κ°μ νΉμ ν λ°μ΄ν° νμμ κ°μ§λλ°,
>
> - ν¬κ² μμ νμ(Primitive type)κ³Ό μ°Έμ‘° νμ(Reference type)μΌλ‘ λΆλ₯
>
>   1. μμ νμ
>
>      - Number, String, Boolean, undefined, null, Symbol
>
>   2. μ°Έμ‘° νμ π Objects
>
>      - κ°μ²΄(Objects) νμμ μλ£ν
>        - λ³μμ ν΄λΉ κ°μ²΄μ μ°Έμ‘° κ°μ΄ λ΄κΈ°κ³ , μ°Έμ‘° κ°μ λ³΅μ¬
>
>      - Array, Function, Object, ...



### 1. Primitive Type

> - κ°μ²΄(Objects)κ° μλ κΈ°λ³Έ νμ
>
> - λ³μμ ν΄λΉ νμμ κ°μ΄ λ΄κΈ°κ³ , μ€μ  κ°μ λ³΅μ¬



#### 1. Number

- μ μ, μ€μ κ΅¬λΆμ΄ μλ νλμ μ«μ νμ
  - λΆλμμμ  νμ
  - cf. `NaN`(Not-A-Number)
    - κ³μ° λΆκ°λ₯ν κ²½μ° λ°νλλ κ°



#### 2. String

- νμ€νΈ λ°μ΄ν°λ₯Ό λνλ΄λ νμ

  - 16λΉνΈ μ λμ½λ λ¬Έμμ μ§ν©

- ννλ¦Ώ λ¦¬ν°λ΄ (Template Literal)

  - backtick(`) μΌλ‘ νν

  - `${ expression } ννλ‘ ννμ μ½μ

    ```javascript
    const name = 'Pepper'
    const age = 5
    const introduce = `${name} is ${age} years old.`
    ```



#### 3. undefined & null

| undefined                                                    | null                                               |
| ------------------------------------------------------------ | -------------------------------------------------- |
| λΉ κ°μ νννκΈ° μν λ°μ΄ν° νμ                            | λΉ κ°μ νννκΈ° μν λ°μ΄ν° νμ                  |
| λ³μ μ μΈ μ΄ν μ§μ  κ°μ ν λΉνμ§ μμΌλ©΄ μλμΌλ‘ `undefined`κ° ν λΉ | κ°λ°μκ° λΉ κ°μ νννκΈ° μν΄ **μλμ μΌλ‘ **ν λΉ |
| `typeof undefined` κ²°κ³Ό κ°μ `undefined`                     | `typeof null` κ²°κ³Ό κ°μ κ°μ²΄(`object`)             |



#### 4. Boolean

- λΌλ¦¬μ  μ°Έ/κ±°μ§μ λνλ΄λ νμ

  - true/falseλ‘ νν

- μ‘°κ±΄λ¬Έ λλ λ°λ³΅λ¬Έμμ μ μ©νκ² μ¬μ©

  - cf. μλ νλ³ν κ·μΉ

    |  Data Type  |    true     |   false    |
    | :---------: | :---------: | :--------: |
    | `undefined` |      -      | ν­μ κ±°μ§  |
    |   `null`    |      -      | ν­μ κ±°μ§  |
    |   Number    | λλ¨Έμ§ κ²½μ° | 0, -0, NaN |
    |   String    | λλ¨Έμ§ κ²½μ° | λΉ λ¬Έμμ΄  |
    |   Object    |   ν­μ μ°Έ   |     -      |

    

### 2. μ°μ°μ

#### 1. ν λΉ μ°μ°μ

- λ€μν μ°μ°μ λν λ¨μΆ μ°μ°μ μ§μ

  ```javascript
  // 1. κΈ°λ³Έ ν λΉ
  let x = 0
  
  // 2. μ¬μΉμ°μ°
  x += 1
  x -= 2
  x *= 3
  x /= 4
  
  // 3. Increment & Decrement μ°μ°μ
  x++ // += 1 κ³Ό λμΌ
  x-- // -= 1 κ³Ό λμΌ
  ```

  

#### 2. λΉκ΅ μ°μ°μ

- νΌμ°μ°μ(μ«μ, λ¬Έμ, Boolean λ±)λ₯Ό λΉκ΅νκ³  λΉκ΅μ κ²°κ³Όκ°μ BooleanμΌλ‘ λ°ννλ μ°μ°μ
- λ¬Έμμ΄μ μ λμ½λ κ°μ μ¬μ©νλ©° νμ€ μ¬μ μμλ₯Ό κΈ°λ°μΌλ‘ λΉκ΅
  - μνλ²³λΌλ¦¬ λΉκ΅ν  κ²½μ°
    - μνλ²³ μ€λ¦μ°¨μμΌλ‘ μ°μ μμλ₯Ό μ§λ
    - μλ¬Έμκ° λλ¬Έμλ³΄λ€ μ°μ μμλ₯Ό μ§λ



#### 3. λλ± λΉκ΅ μ°μ°μ (`==`)

- λ νΌμ°μ°μκ° κ°μ κ°μΌλ‘ νκ°λλμ§ λΉκ΅ ν Boolean κ° λ°ν
  - **μλ¬΅μ  νμ λ³ν**μ ν΅ν΄ νμμ μΌμΉμν¨ ν κ°μ κ°μΈμ§ λΉκ΅
    - μμμΉ λͺ»ν κ²°κ³Όκ° λ°μν  μ μμΌλ―λ‘ νΉλ³ν κ²½μ°λ₯Ό μ μΈνκ³  μ¬μ©νμ§ μμ
  - λ νΌμ°μ°μκ° λͺ¨λ κ°μ²΄μΌ κ²½μ°, λ©λͺ¨λ¦¬μ κ°μ κ°μ²΄λ₯Ό λ°λΌλ³΄λμ§ νλ³



#### 4. μΌμΉ λΉκ΅ μ°μ°μ (`===`)

- λ νΌμ°μ°μκ° β  κ°μ νμμΈμ§ νμΈνκ³  β‘ κ°μ κ°μΌλ‘ νκ°λλμ§ λΉκ΅ ν Boolean κ° λ°ν
  - **μκ²©ν λΉκ΅**κ° μ΄λ€μ§λ©° μλ¬΅μ  νμ λ³νμ΄ λ°μνμ§ μμ
  - λ νΌμ°μ°μκ° λͺ¨λ κ°μ²΄μΌ κ²½μ°, λ©λͺ¨λ¦¬μ κ°μ κ°μ²΄λ₯Ό λ°λΌλ³΄λμ§ νλ³



#### 5. λΌλ¦¬ μ°μ°μ

- μΈ κ°μ§ λΌλ¦¬ μ°μ°μλ‘ κ΅¬μ±
  - and μ°μ°μ `&&` μ°μ°μ
  - or μ°μ°μ `||` μ°μ°μ
  - not μ°μ°μ `!` μ°μ°μ



#### 6. μΌν­ μ°μ°μ

- μΈ κ°μ νΌμ°μ°μλ₯Ό μ¬μ©νμ¬ μ‘°κ±΄μ λ°λΌ κ°μ λ°ννλ μ°μ°μ

  - `condition ? optionA : optionB`

    - μ‘°κ±΄μμ΄ μ°Έμ΄λ©΄ A κ°μ, κ±°μ§μ΄λ©΄ B κ°μ μ¬μ©

  - μΌν­ μ°μ°μμ κ²°κ³Όλ λ³μμ ν λΉ κ°λ₯

  - ν μ€μ νκΈ°νλ κ²μ κΆμ₯

    ```javascript
    console.log(true ? 1 : 2) // β 1
    console.log(false ? 1 : 2) // β 2
    ```

    

## 3. Control flow

### 1. Conditions

#### 1. if statement

- μ‘°κ±΄ ννμμ κ²°κ³Όκ°μ Boolean νμμΌλ‘ λ³ν ν μ°Έ/κ±°μ§ νλ¨

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

- μ‘°κ±΄ ννμμ κ²°κ³Ό κ°μ΄ μ΄λ κ°(case)μ ν΄λΉνλμ§ νλ³

  - μ£Όλ‘ νΉμ  λ³μμ κ°μ λ°λΌ μ‘°κ±΄μ λΆκΈ°ν  λ νμ©
    - μ‘°κ±΄μ΄ λ§μμ§ κ²½μ°, ifλ¬Έλ³΄λ€ κ°λμ±μ΄ λμ μ μμ

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

  - `break`, `default` λ¬Έμ μ νμ μΌλ‘ μ¬μ© κ°λ₯
    - breakλ¬Έμ΄ μλ κ²½μ°,  breakλ¬Έμ λ§λκ±°λ defaultλ¬Έμ μ€νν  λκΉμ§ λ€μ μ‘°κ±΄λ¬Έ μ€ν



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
  console.log('μ¬λ°λ₯Έ μ°μ°μλ₯Ό μλ ₯ν΄μ£ΌμΈμ.')
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
    console.log('μ¬λ°λ₯Έ μ°μ°μλ₯Ό μλ ₯ν΄μ£ΌμΈμ.')
  }
}
```



### 2. Loops

#### 1. while

- μ‘°κ±΄λ¬Έμ΄ μ°ΈμΈ λμ λ°λ³΅ μν

  ```javascript
  let num = 0
  
  while (num < 10) {
    console.log(num)
    num += 1
  }
  ```

  

#### 2. for

- μΈλ―Έμ½λ‘  `;` μΌλ‘ κ΅¬λΆλλ μΈ λΆλΆμΌλ‘ κ΅¬μ±

  - initialization : μ΅μ΄ λ°λ³΅λ¬Έ μ§μ μ 1νλ§ μ€ν

  - condition : λ§€ λ°λ³΅ μν μ  νκ°λλ λΆλΆ

  - expression : λ§€ λ°λ³΅ μν μ΄ν νκ°λλ λΆλΆ

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

- κ°μ²΄(object)μ μμ±λ€μ μνν  λ μ¬μ©

  - λ°°μ΄ μνλ κ°λ₯νλ κΆμ₯νμ§ μμ

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

- λ°λ³΅ κ°λ₯ν(iterable) κ°μ²΄λ₯Ό μννλ©° κ°μ κΊΌλΌ λ μ¬μ©

  ```javascript
  const animals = ['Pepper', 'Kanda', 'Tony']
  
  for (let animal of animals) {
      console.log(animal)
  }
  ```

  

## 4. Function

> - μλ°μ€ν¬λ¦½νΈ ν¨μλ μΌκΈ κ°μ²΄(First-class citizens)
>   - λ³μμ ν λΉ κ°λ₯
>   - ν¨μμ λ§€κ°λ³μλ‘ μ λ¬ κ°λ₯
>   - ν¨μμ λ°ν κ°μΌλ‘ μ¬μ© κ°λ₯



### 1. ν¨μ μ μΈμ

- ν¨μμ μ΄λ¦κ³Ό ν¨κ» μ μνλ λ°©μ

  - μ΅λͺ ν¨μ λΆκ°λ₯, νΈμ΄μ€ν O

  ```javascript
  function name (args) {
      // do something 
  }
  ```

  

### 2. ν¨μ ννμ

- νμλ₯Ό ννμ λ΄μμ μ μνλ λ°©μ

  - ν¨μ μ΄λ¦μ μλ΅νκ³  μ΅λͺ ν¨μλ‘ μ μ κ°λ₯, νΈμ΄μ€ν X
  - Airbnb Style Guide κΆμ₯ λ°©μ

  ```javascript
  const myFunction = function (args) {
      // do something
  }
  ```

  

#### cf. ν¨μ μ μΈμ vs ν¨μ ννμ

1. νΈμ΄μ€ν

   ```javascript
   // 1. ν¨μ μ μΈμ π νΈμ΄μ€ν O
   
   plus(2, 5) // β 7
   
   function plus (num1, num2) {
       return num1 + num2
   }
   
   // 2. ν¨μ ννμ π νΈμ΄μ€ν X
   minus(5, 2) // β Uncaught ReferenceError
   
   const minus = function (num1, num2) {
       return num1 - num2
   }
   ```

   

### 3. νμ΄ν ν¨μ (Arrow Function)

- ν¨μλ₯Ό λΉκ΅μ  κ°κ²°νκ² μ μν  μ μλ λ¬Έλ²

  1. function ν€μλ μλ΅ κ°λ₯

  2. ν¨μμ **λ§€κ°λ³μκ° νλ** λΏμ΄λ©΄ `()`λ μλ΅ κ°λ₯
  3. ν¨μ λ°λμ ννμ νλλΌλ©΄ `{}`κ³Ό `return` μλ΅ κ°λ₯

- [example]

  ```javascript
  // 0. ν¨μ ννμ
  const greeting = function (name) {
      return `hello, ${name}`
  }
  
  // 1. function μλ΅
  const greeting = (name) => { return `hello, ${name}` }
  
  // 2. () μλ΅
  const greeting = name => { return `hello, ${name}` }
  
  // 3. {} & return μλ΅
  const greeting = name => `hello, ${name}`
  ```

  

## 5. Arrays & Objects

### 1. Arrays

> ν€μ μμ±λ€μ λ΄κ³  μλ μ°Έμ‘° νμμ κ°μ²΄(object)
>
> - μμ λ³΄μ₯
> - 0μ ν¬ν¨ν μμ μ μ μΈλ±μ€λ‘ νΉμ  κ°μ μ κ·Ό
> - λ°°μ΄μ κΈΈμ΄λ `array.length`λ‘ μ κ·Ό



#### 1. κΈ°λ³Έ λ°°μ΄ μ‘°μ Method

| Method          | Description                                          | etc.                    |
| --------------- | ---------------------------------------------------- | ----------------------- |
| reverse         | μλ³Έ λ°°μ΄μ μμλ€μ μμλ₯Ό λ°λλ‘ μ λ ¬              |                         |
| push & pop      | λ°°μ΄μ κ°μ₯ λ€μ μμλ₯Ό μΆκ° λλ μ κ±°               |                         |
| unshift & shift | λ°°μ΄μ κ°μ₯ μμ μμλ₯Ό μΆκ° λλ μ κ±°               |                         |
| includes        | λ°°μ΄μ νΉμ  κ°μ΄ μ‘΄μ¬νλμ§ νλ³ ν μ°Έ/κ±°μ§ λ°ν     |                         |
| indexOf         | λ°°μ΄μ νΉμ  κ°μ΄ μ‘΄μ¬νλμ§ νλ³ ν ν΄λΉ μΈλ±μ€ λ°ν | μμ κ²½μ° -1 λ°ν       |
| join            | λ°°μ΄μ λͺ¨λ  μμλ₯Ό κ΅¬λΆμλ₯Ό λ§€κ°λ‘ μ°κ²°              | κ΅¬λΆμ μλ΅ μ μΌν `,` |
| splice          | λ°°μ΄μ μμλ₯Ό μΆκ°γ»μ­μ γ»κ΅μ²΄                       |                         |

```js
// splice(νΉμ  μ§μ  idx, μ­μ ν  κ°―μ[, μΆκ°ν  μμ])
const months = ['Jan', 'Mar', 'Apr', 'Jun']

months.splice(1, 0, 'Feb')
console.log(months) // ['Jan', 'Feb', 'Mar', 'Apr', 'Jun']

months.splice(4, 1, 'May')
console.log(months) // ['Jan', 'Feb', 'Mar', 'Apr', 'May']
```



#### 2. Array Helper Methods

- λ°°μ΄μ μννλ©° νΉμ  λ‘μ§μ μννλ λ©μλ
- λ©μλ νΈμΆ μ μΈμλ‘ callback ν¨μλ₯Ό λ°λ κ²μ΄ νΉμ§
  - callback ν¨μ: μ΄λ€ ν¨μμ λ΄λΆμμ μ€νλ  λͺ©μ μΌλ‘ μΈμλ‘ λκ²¨λ°λ ν¨μ

| Method  | Description                                                  |
| ------- | ------------------------------------------------------------ |
| forEach | λ°°μ΄μ κ° μμμ λν΄ μ½λ°± ν¨μλ₯Ό ν λ²μ© μ€ν (λ°ν κ° μμ) |
| map     | μ½λ°± ν¨μμ λ°ν κ°μ μμλ‘ νλ μλ‘μ΄ λ°°μ΄ λ°ν           |
| filter  | μ½λ°± ν¨μμ λ°ν κ°μ΄ `true`μΈ μμλ€λ§ λͺ¨μ μλ‘μ΄ λ°°μ΄ λ°ν |
| reduce  | μ½λ°± ν¨μμ λ°ν κ°λ€μ νλμ κ°(acc)μ λμ  ν λ°ν        |
| find    | μ½λ°± ν¨μμ λ°ν κ°μ΄ `true`λ©΄ ν΄λΉ μμλ₯Ό λ°ν              |
| some    | λ°°μ΄μ μμ μ€ **νλ**λΌλ νλ³ ν¨μλ₯Ό ν΅κ³Όνλ©΄ `true`λ₯Ό λ°ν |
| every   | λ°°μ΄μ **λͺ¨λ  μμ**κ° νλ³ ν¨μλ₯Ό ν΅κ³Όνλ©΄ `true`λ₯Ό λ°ν    |

- `array.forEach(callback(element[, index[, array]]))`

  - break, continue μ¬μ© λΆκ°λ₯

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
  
  console.log(doulbleNums) // π [2, 4, 6, 8, 10]
  console.log(oddNums) // π [1, 3, 5]
  ```



- `array.reduce(callback(acc, element, [index[, array]])[, initialValue])`

  - `acc` : μ΄μ  callback ν¨μμ λ°ν κ°μ΄ λμ λλ λ³μ
  - `initialValue` : callback ν¨μ μ΅μ΄ νΈμΆ μ, accμ ν λΉλλ κ°
    - μ€μ νμ§ μμΌλ©΄ λ°°μ΄μ μ²« λ²μ§Έ κ°μΌλ‘ μ¬μ©

  ```javascript
  const nums = [1, 2, 3, 4, 5]
  
  const sumOfNums = nums.reduce((acc, num) => {
      return acc + num
  }, 0)
  
  console.log(sumOfNums) // π 15
  ```

  

- `array.find(callback(element[, index[, array]]))`

  - μ°Ύλ κ°μ΄ λ°°μ΄μ μμΌλ©΄ `undefined` λ°ν

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
  
  console.log(result) // π { name: 'Carol', score: 100}
  ```

  

- `array.some(callback(element[, index[, array]]))`

  - λΉ λ°°μ΄μ ν­μ `false`

- `array.every(callback(element[, index[, array]]))`

  - λΉ λ°°μ΄μ ν­μ `true`

  ```javascript
  const nums = [1, 2, 3, 4, 5]
  
  const hasOddNum = nums.some((num) => {
      return num % 2
  })
  
  const isEveryNumsOdd = nums.every((num) => {
      return num % 2
  })
  ```

  

#### 3. λ°°μ΄ μν λ°©μ

```javascript
const animals = ['Cat', 'Dog', 'Lion', 'Tiger', 'Snake', 'Bird']

// 1. for loop (breakλ¬Έ μ¬μ© κ°λ₯)
for (let i = 0; i < animals.length; i++) {
    console.log(i, animals[i])
}

// 2. for - of
for (animal of animals) {
    console.log(animal)
}

// 3. forEach (breakλ¬Έ μ¬μ© λΆκ°λ₯)
animals.forEach((animal, index) => {
    console.log(index, animal)
})
```



### 2. Objects

> μμ±μ μ§ν©μΌλ‘, μ€κ΄νΈ λ΄λΆμ key-value μμΌλ‘ νν 
>
> - keyλ λ¬Έμμ΄ νμ (κ΅¬λΆμκ° μμ κ²½μ° λ°μ΄νλ‘ λ¬Άμ΄μ νν)
> - valueλ λͺ¨λ  νμ



 #### 1. κ°μ²΄ μμ± λ° μ‘°μ λ¬Έλ²

1. μμ±λͺ μΆμ½

   - κ°μ²΄ μ μ μ, keyμ ν λΉνλ λ³μ μ΄λ¦μ΄ κ°μΌλ©΄ μΆμ½ κ°λ₯

     ```javascript
     let fruits = ['apple', 'orange', 'banana', 'lemon']
     let vagetables = ['mushroom']
     
     const market = {
         fruits,
         vegetables,
     }
     ```

     

2. λ©μλλͺ μΆμ½

   - λ©μλ μ μΈμ function ν€μλ μλ΅ κ°λ₯

     ```javascript
     const greeting = {
         hello() {
             console.log('Hello!')
         }
     }
     ```

     

3. κ³μ°λ μμ± μ¬μ©

   - κ°μ²΄ μ μ μ key μ΄λ¦μ ννμμ ν΅ν΄ λμ μΌλ‘ μμ± κ°λ₯

     ```javascript
     const firstCat = 'pepper'
     const secondCat = 'kanda'
     const myCats = {
         [firstCat]: 5,
         [secondCat.toUpperCase()]: 3,
     }
     
     console.log(myCats) // π {pepper: 5, KANDA: 3}
     ```

     

4. κ΅¬μ‘° λΆν΄ ν λΉ

   - λ°°μ΄ λλ κ°μ²΄λ₯Ό λΆν΄νμ¬ μμ±μ λ³μμ μ½κ² ν λΉν  μ μλ λ¬Έλ²

     - keyμ λ³μ λͺμ΄ κ°μ κ²½μ° μ¬μ© κ°λ₯

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
> - key-value μ ννμ λ°μ΄ν°λ₯Ό νκΈ°νλ μΈμ΄ λλ¦½μ  νμ€ ν¬λ§·
>   - μλ°μ€ν¬λ¦½νΈ κ°μ²΄(objects)μ μ μ¬νκ² μκ²ΌμΌλ, μ€μ λ‘λ **λ¬Έμμ΄ νμ**
> - JSONμ μ‘°μνκΈ° μν λ κ°μ§ λ΄μ₯ λ©μλ
>   - `JSON.parse()` π JSON > μλ°μ€ν¬λ¦½νΈ κ°μ²΄
>   - `JSON.stringify()` π μλ°μ€ν¬μνΈ κ°μ²΄ > JSON





## * `this` in JavaScript

> ν¨μ νΈμΆ λ°©μμ μν΄ κ²°μ λλ `this`
>
> - μλ°μ€ν¬λ¦½νΈλ ν΄λΉ ν¨μ νΈμΆ λ°©μμ λ°λΌ thisμ λ°μΈλ©λλ κ°μ²΄κ° λ¬λΌμ§
> - μ¦, ν¨μλ₯Ό μ μΈν  λ thisμ κ°μ²΄κ° κ²°μ λλ κ² μλλΌ, **ν¨μλ₯Ό μ΄λ»κ² νΈμΆνλμ§μ λ°λΌ λμ μΌλ‘ κ²°μ **λλ κ²



### 1. ν¨μ νΈμΆ λ°©μ

#### 1. ν¨μ νΈμΆ

> μ μ­ κ°μ²΄λ λͺ¨λ  κ°μ²΄μ μ μΌν μ΅μμ κ°μ²΄λ₯Ό μλ―Ένλ©°, μΌλ°μ μΌλ‘ Browserμμλ `window`

```js
const checkThis = function () {
    console.log(this)
}

checkThis() // π window
```

- κΈ°λ³Έμ μΈ ν¨μ μ μΈμ νκ³ , μ μ­μμ νΈμΆν  κ²½μ° μ μ­ κ°μ²΄κ° λ°μΈλ©



#### 2. λ©μλ νΈμΆ

```js
const user = {
    name: 'pepper',
    checkThis,
}

user.checkThis() // π {name: "pepper", checkThis: Ζ}
```

- λ©μλλ‘ μ μΈνκ³  νΈμΆν  κ²½μ°, κ°μ²΄μ λ©μλμ΄λ―λ‘ ν΄λΉ κ°μ²΄κ° λ°μΈλ©



#### 3. Arrow Function

> - νμ΄ν ν¨μλ νΈμΆ μμΉμ μκ΄μμ΄ μμ μ€μ½νλ₯Ό κ°λ¦¬ν΄
>   - Lexical scope
>     - ν¨μλ₯Ό μ΄λμ νΈμΆνλμ§κ° μλλΌ **μ΄λμ μ μΈ**νμλμ§μ λ°λΌ κ²°μ 

```js
const checkArrowThis = () => {
    console.log(this)
}

const user = {
    name: 'kanda',
    checkArrowThis,
}

checkArrowThis() // π window
user.checkArrowThis() // π window
```

- λ©μλ μ μΈμ νμ΄ν ν¨μλ‘ νλ©΄, ν΄λΉ κ°μ²΄μ μμ μ€μ½νμΈ μ μ­ κ°μ²΄κ° λ°μΈλ©

  - checkArrowThis() ν¨μκ° μ μ΄μ μ μ­μμ μ μΈλμκΈ° λλ¬Έ

    π **λ©μλ μ μΈμ function ν€μλ**λ₯Ό ν΅ν΄ μ μν΄μΌ ν¨



### 2. ES6μμμ νμ΄ν ν¨μ

#### 1. ν¨μ λ΄ ν¨μ

- function ν€μλ

  ```js
  const zoo = {
      animals: ['Lion'],
      print: function () {
          console.log(this) // {animals: Array(1), print: Ζ}
          console.log(this.animals) // ["Lion"]
          this.animals.forEach(function (animal) {
              console.log(animal) // Lion
              console.log(this) // window
          })
      }
  }
  
  zoo.print()
  ```

  - μ μ­μμ νΈμΆλμκΈ° λλ¬Έμ forEachμ μ½λ°± ν¨μμμ thisμλ μ μ­ κ°μ²΄μΈ window λ°μΈλ©

  

- νμ΄ν ν¨μ

  ```js
  const zoo = {
      animals: ['Lion'],
      print: function () {
          console.log(this) // {animals: Array(1), print: Ζ}
          console.log(this.animals) // ["Lion"]
          this.animals.forEach((animal) => {
              console.log(animal) // Lion
              console.log(this) // {animals: Array(1), print: Ζ}
          })
      }
  }
  
  zoo.print()
  ```

  - print λ©μλ λ΄μ forEachμ μ½λ°±ν¨μμμμ μμ μ€μ½νλ zoo κ°μ²΄

    - νΈμΆ μμΉμ κ΄κ³ μμ΄ μ μΈ μμΉμ μμ μ€μ½νλ₯Ό κ°λ¦¬ν€λ νμ΄ν ν¨μλ thisμ zooκ° λ°μΈλ©

      π **ν¨μ λ΄μ ν¨μ μν©μμλ νμ΄ν ν¨μ**λ₯Ό μ°λ κ²μ΄ μ’μ



#### 2. μ΄λ²€νΈ λ¦¬μ€λ

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

- addEventListenerμμμ μ½λ°± ν¨μλ,

  - νΉλ³νκ² function ν€μλμ κ²½μ°μ μ΄λ²€νΈ λ¦¬μ€λλ₯Ό νΈμΆν λμμ( event.target ) λ»ν¨

    π λ°λΌμ, νΈμΆν λμμ μνλ€λ©΄ this λ₯Ό νμ©ν  μ μμ

  - λ€λ§, νμ΄ν ν¨μμ κ²½μ° μμ μ€μ½νλ₯Ό μ§μΉ­νκΈ° λλ¬Έμ window κ°μ²΄κ° λ°μΈλ© λ¨

- **μ΄λ²€νΈ λ¦¬μ€λμ μ½λ°± ν¨μλ function ν€μλ**λ₯Ό μ¬μ©