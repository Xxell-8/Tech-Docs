# TypeScript 🐬

> #### INDEX
>
> 1. [TypeScript 시작하기](#INTRO)
> 1. [Type 알아보기](#Type)



## INTRO

#### 1. TypeScript란

- 자바스크립트(JS)에 타입을 부여한, JS의 확장된 언어

  - 자바스크립트의 상위 집합으로 ECMA 스크립트의 최신 표준을 지원

  - 브라우저 실행을 위해 컴파일(compile) 과정이 필요
  - 정적인 언어로 컴파일 시간에 타입을 검사
    - 터미널에서 `tsc <파일명>` 명령을 통해 JS 파일로 컴파일 가능

- **WHY** TypeScript?
  - 강력한 타입으로 대규모 애플리케이션 개발에 용이
    - 에러의 사전 방지
    - 코드 자동 완성과 가이드
  - 유명한 자바스크립트 라이브러리와의 편리한 사용
  - 개발 도구에서의 강력한 지원



#### 2. JS Doc vs TS

- JS Doc을 활용하면 자바 스크립트를 타입 스크립트처럼 활용 가능

  ```js
  // @ts-check
  /**
   * 
   * @param {number} a 첫번째 숫자
   * @param {number} b 두번째 숫자
   * @returns {number} 합산 값
   */
  function sum(a, b) {
    return a + b;
  }
  
  sum(10, '20'); 
  // Argument of type 'string' is not assignable to parameter of type 'number'.ts(2345)
  ```

- TS를 활용하면 좀 더 편리하게 타입을 정의하고, 코드 효율성을 높일 수 있음

  ```typescript
  function add(a: number, b: number): number {
    return a + b;
  }
  
  let result = add(10, 20);
  // ts가 result의 타입을 추론해 number 타입에서 활용할 수 있는 메서드를 자동 완성 시켜줌
  result.toLocaleString();
  
  add(10, '20'); 
  // Argument of type 'string' is not assignable to parameter of type 'number'.ts(2345)
  ```

  

#### 3. 컴파일 하기

- TypeScript로 작성된 파일을 브라우저에서 동작시키기 위해 JS 파일로 컴파일

  - 기본 명령은 `tsc <file name>`

  - 옵션을 통해 원하는 버전이나 모듈 등을 지정할 수 있음

    ```bash
    // js 버전 지정
    tsc hello.ts --target es6
    
    // 라이브러리 지정
    tsc hello.ts --lib es5,es2015.promise,es2015.iterable,dom
    tsc hello.ts --lib es2015,dom
    
    // 모듈 지정
    tsc hello.ts --target es6 -lib es2015,dom --module commonjs
    
    // 옵션 확인
    tsc hello.ts --target es6 -lib es2015,dom --module commonjs --showConfig
    ```

- 프로젝트 루트 폴더에 `tsconfig.json` 파일을 작성해 컴파일러 설정 가능

  - [tsconfig 속성 알아보기](https://www.typescriptlang.org/tsconfig)
  
  ```json
  {
    	// 컴파일할 파일 지정
      "include": [
          "src/**/*.ts"
      ],
    	// 컴파일에 제외할 파일 지정
      "exclude": [
          "node_modules"
      ],
      "compilerOptions": {
          "module": "es6",
          "rootDir": "src",
          "outDir": "dist",
          "target": "es5",
          // 소스 파일 표시
          "sourceMap": true,
          // 주석 자동 제거
          "removeComments": true,
          // 명시적인 타입 지정 필수
          "noImplicitAny": true,
      },
  }
  ```
  



## Type

#### 1. 기본 타입

| Types     | Code                                                         | etc.                                    |
| --------- | ------------------------------------------------------------ | --------------------------------------- |
| Boolean   | `let booleanValue: boolean = false`                          |                                         |
| Number    | `let numValue: number =  100`                                |                                         |
| String    | `let stringValue: string = 'world'`                          |                                         |
| Symbol    | `let symbolValue: symbol = Symbol()`                         |                                         |
| Object    | `let objValue: object = {}`<br />`let userInfo: { id: number, name: string } = { id: 1, name: 'user' }` |                                         |
| Array     | `let arrValue: number[] = [1, 2, 3]`<br />`let arrValue: Array<number> = [1, 2, 3]` |                                         |
| Tuple     | `let tupleValue: [string, number] = ['user', 1]`             |                                         |
| Enum      | `enum Role { Admin, SystemManager, User }`                   |                                         |
| Any       | `let anyValue: any = 10`<br />`let anyValue: any = 'Hello'`<br />`let anyValue: any = true` | 모든 타입에 대해 허용                   |
| Void      | `let voidValue: void = undefined`<br />`function voidFunc(): void {}` | 변수는 `undefined`와 `null`만 할당      |
| Undefined | `let undefinedValue: undefined`                              |                                         |
| Null      | `let nullValue: null`                                        |                                         |
| Never     | `function neverEnd(): never {}`                              | 함수의 끝에 절대 도달하지 않는다는 의미 |



#### 2. Function

> - 함수의 경우, 크게 3가지의 타입을 정의할 수 있음
>   - 함수의 Parameter(매개변수)
>   - 함수의 반환 타입
>   - 함수의 구조 타입

```typescript
// 함수의 파라미터와 반환 타입 지정
function add(x: number, y: number): number {
    return x + y
}

// 옵셔널 파라미터(?)
function log(id: number, message?: string) {
  if (message) {
    console.log(`${id}번 사용자: ${message}`)
    return;
  }
  console.log(`${id}번 사용자 입장`)
}

// 파라미터 기본 값 설정
function getOption(key: number = 0) {
  return options[key]
}

// 함수의 구조
interface Storage {
    a: string
}
interface ColdStorage {
    b: string
}

function store(type: "칸다"): Storage
function store(type: "후추"): ColdStorage

function store(type: "칸다" | "후추") {
    if (type === "칸다") {
        return { a: "kanda" }
    }
  	if (type === "후추") {
        return { b: "pepper" }
    }
    
    throw new Error('unsupported type')
}
```



#### 3. Interface

```typescript
// 객체 스펙 정의
interface User {
  id: number;
  name: string;
}

let user1: User = {
  name: 'username',
  id: 10
}

// 인터페이스 확장
interface Admin extends User {
  code: number
}

let admin: Admin = {
  id: 12312,
  name: 'admin_user',
  code: 102834578
}

// 함수 타입 정의
interface Login {
  (username: string, password: string): boolean;
}

let onLogin: Login = function (username: string, password: string) {
  if isValid(username, password) {
    return true;
  }
  return false;
}

// 클래스 타입 정의
interface ApiService {
  data: any[];
  getData(id?: number): void;
}

class UserApi implements ApiService {
  BASE_URL = 'api.something.com/users/'
  data: any[];
  
  constructor() {
    
  }
  
  getData(id?: number) {
    const url = id ? BASE_URL + id : BASE_URL
    fetch(url)
    	.then(res => res.json())
    	.then(data => this.data = data)
  }
}
```



#### 4. Enum

```typescript
enum Level {
    WELCOME = "WC",
    GREEN = "GR",
    GOLD = "GD"
}

function getDiscount(v: Level): number {
    switch (v) {
        case Level.WELCOME:
            return 1;
        case Level.GREEN:
            return 5;
        case Level.GOLD:
            return 10;
    }
}

console.log(getDiscount(Level.GOLD));
console.log(Level.GOLD);
```



#### 5. Union & Intersection

- 유니온 타입은 `OR(||)` 연산자와 같이 여러 개의 타입이 올 수 있는 경우 사용

  ```typescript
  function printLog(log: string | number) {
  	if (typeof log === 'string') {
      console.log(log)
    }
    if (typeof log === 'number') {
      console.log('code: ' + log)
    }
    throw new TypeError('value must be string or number')
  }
  ```

- 유니온 타입과 인터섹션 타입 비교

  ```typescript
  interface Person {
    name: string;
    job: string;
  }
  
  interface Animal {
    name: string;
    species: string;
  }
  
  // 유니온 타입의 경우, 사용된 타입들의 공통 속성만 이용 가능
  function getInfo(target: Person | Animal) {
    console.log(target.name);
  }
  
  // 인터섹션 타입의 경우, 사용된 타입의 모든 속성을 가진 새로운 타입이 생성됨
  const someone: Person & Animal = {
    name: 'John Doe',
    species: 'Human',
    job: 'Student'
  };
  ```

  
