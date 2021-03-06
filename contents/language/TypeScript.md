# TypeScript π¬

> #### INDEX
>
> 1. [TypeScript μμνκΈ°](#INTRO)
> 1. [Type μμλ³΄κΈ°](#Type)



## INTRO

#### 1. TypeScriptλ

- μλ°μ€ν¬λ¦½νΈ(JS)μ νμμ λΆμ¬ν, JSμ νμ₯λ μΈμ΄

  - μλ°μ€ν¬λ¦½νΈμ μμ μ§ν©μΌλ‘ ECMA μ€ν¬λ¦½νΈμ μ΅μ  νμ€μ μ§μ

  - λΈλΌμ°μ  μ€νμ μν΄ μ»΄νμΌ(compile) κ³Όμ μ΄ νμ
  - μ μ μΈ μΈμ΄λ‘ μ»΄νμΌ μκ°μ νμμ κ²μ¬
    - ν°λ―Έλμμ `tsc <νμΌλͺ>` λͺλ Ήμ ν΅ν΄ JS νμΌλ‘ μ»΄νμΌ κ°λ₯

- **WHY** TypeScript?
  - κ°λ ₯ν νμμΌλ‘ λκ·λͺ¨ μ νλ¦¬μΌμ΄μ κ°λ°μ μ©μ΄
    - μλ¬μ μ¬μ  λ°©μ§
    - μ½λ μλ μμ±κ³Ό κ°μ΄λ
  - μ λͺν μλ°μ€ν¬λ¦½νΈ λΌμ΄λΈλ¬λ¦¬μμ νΈλ¦¬ν μ¬μ©
  - κ°λ° λκ΅¬μμμ κ°λ ₯ν μ§μ



#### 2. JS Doc vs TS

- JS Docμ νμ©νλ©΄ μλ° μ€ν¬λ¦½νΈλ₯Ό νμ μ€ν¬λ¦½νΈμ²λΌ νμ© κ°λ₯

  ```js
  // @ts-check
  /**
   * 
   * @param {number} a μ²«λ²μ§Έ μ«μ
   * @param {number} b λλ²μ§Έ μ«μ
   * @returns {number} ν©μ° κ°
   */
  function sum(a, b) {
    return a + b;
  }
  
  sum(10, '20'); 
  // Argument of type 'string' is not assignable to parameter of type 'number'.ts(2345)
  ```

- TSλ₯Ό νμ©νλ©΄ μ’ λ νΈλ¦¬νκ² νμμ μ μνκ³ , μ½λ ν¨μ¨μ±μ λμΌ μ μμ

  ```typescript
  function add(a: number, b: number): number {
    return a + b;
  }
  
  let result = add(10, 20);
  // tsκ° resultμ νμμ μΆλ‘ ν΄ number νμμμ νμ©ν  μ μλ λ©μλλ₯Ό μλ μμ± μμΌμ€
  result.toLocaleString();
  
  add(10, '20'); 
  // Argument of type 'string' is not assignable to parameter of type 'number'.ts(2345)
  ```

  

#### 3. μ»΄νμΌ νκΈ°

- TypeScriptλ‘ μμ±λ νμΌμ λΈλΌμ°μ μμ λμμν€κΈ° μν΄ JS νμΌλ‘ μ»΄νμΌ

  - κΈ°λ³Έ λͺλ Ήμ `tsc <file name>`

  - μ΅μμ ν΅ν΄ μνλ λ²μ μ΄λ λͺ¨λ λ±μ μ§μ ν  μ μμ

    ```bash
    // js λ²μ  μ§μ 
    tsc hello.ts --target es6
    
    // λΌμ΄λΈλ¬λ¦¬ μ§μ 
    tsc hello.ts --lib es5,es2015.promise,es2015.iterable,dom
    tsc hello.ts --lib es2015,dom
    
    // λͺ¨λ μ§μ 
    tsc hello.ts --target es6 -lib es2015,dom --module commonjs
    
    // μ΅μ νμΈ
    tsc hello.ts --target es6 -lib es2015,dom --module commonjs --showConfig
    ```

- νλ‘μ νΈ λ£¨νΈ ν΄λμ `tsconfig.json` νμΌμ μμ±ν΄ μ»΄νμΌλ¬ μ€μ  κ°λ₯

  - [tsconfig μμ± μμλ³΄κΈ°](https://www.typescriptlang.org/tsconfig)
  
  ```json
  {
    	// μ»΄νμΌν  νμΌ μ§μ 
      "include": [
          "src/**/*.ts"
      ],
    	// μ»΄νμΌμ μ μΈν  νμΌ μ§μ 
      "exclude": [
          "node_modules"
      ],
      "compilerOptions": {
          "module": "es6",
          "rootDir": "src",
          "outDir": "dist",
          "target": "es5",
          // μμ€ νμΌ νμ
          "sourceMap": true,
          // μ£Όμ μλ μ κ±°
          "removeComments": true,
          // λͺμμ μΈ νμ μ§μ  νμ
          "noImplicitAny": true,
      },
  }
  ```
  



## Type

#### 1. κΈ°λ³Έ νμ

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
| Any       | `let anyValue: any = 10`<br />`let anyValue: any = 'Hello'`<br />`let anyValue: any = true` | λͺ¨λ  νμμ λν΄ νμ©                   |
| Void      | `let voidValue: void = undefined`<br />`function voidFunc(): void {}` | λ³μλ `undefined`μ `null`λ§ ν λΉ      |
| Undefined | `let undefinedValue: undefined`                              |                                         |
| Null      | `let nullValue: null`                                        |                                         |
| Never     | `function neverEnd(): never {}`                              | ν¨μμ λμ μ λ λλ¬νμ§ μλλ€λ μλ―Έ |



#### 2. Function

> - ν¨μμ κ²½μ°, ν¬κ² 3κ°μ§μ νμμ μ μν  μ μμ
>   - ν¨μμ Parameter(λ§€κ°λ³μ)
>   - ν¨μμ λ°ν νμ
>   - ν¨μμ κ΅¬μ‘° νμ

```typescript
// ν¨μμ νλΌλ―Έν°μ λ°ν νμ μ§μ 
function add(x: number, y: number): number {
    return x + y
}

// μ΅μλ νλΌλ―Έν°(?)
function log(id: number, message?: string) {
  if (message) {
    console.log(`${id}λ² μ¬μ©μ: ${message}`)
    return;
  }
  console.log(`${id}λ² μ¬μ©μ μμ₯`)
}

// νλΌλ―Έν° κΈ°λ³Έ κ° μ€μ 
function getOption(key: number = 0) {
  return options[key]
}

// ν¨μμ κ΅¬μ‘°
interface Storage {
    a: string
}
interface ColdStorage {
    b: string
}

function store(type: "μΉΈλ€"): Storage
function store(type: "νμΆ"): ColdStorage

function store(type: "μΉΈλ€" | "νμΆ") {
    if (type === "μΉΈλ€") {
        return { a: "kanda" }
    }
  	if (type === "νμΆ") {
        return { b: "pepper" }
    }
    
    throw new Error('unsupported type')
}
```



#### 3. Interface

```typescript
// κ°μ²΄ μ€ν μ μ
interface User {
  id: number;
  name: string;
}

let user1: User = {
  name: 'username',
  id: 10
}

// μΈν°νμ΄μ€ νμ₯
interface Admin extends User {
  code: number
}

let admin: Admin = {
  id: 12312,
  name: 'admin_user',
  code: 102834578
}

// ν¨μ νμ μ μ
interface Login {
  (username: string, password: string): boolean;
}

let onLogin: Login = function (username: string, password: string) {
  if isValid(username, password) {
    return true;
  }
  return false;
}

// ν΄λμ€ νμ μ μ
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

- μ λμ¨ νμμ `OR(||)` μ°μ°μμ κ°μ΄ μ¬λ¬ κ°μ νμμ΄ μ¬ μ μλ κ²½μ° μ¬μ©

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

- μ λμ¨ νμκ³Ό μΈν°μΉμ νμ λΉκ΅

  ```typescript
  interface Person {
    name: string;
    job: string;
  }
  
  interface Animal {
    name: string;
    species: string;
  }
  
  // μ λμ¨ νμμ κ²½μ°, μ¬μ©λ νμλ€μ κ³΅ν΅ μμ±λ§ μ΄μ© κ°λ₯
  function getInfo(target: Person | Animal) {
    console.log(target.name);
  }
  
  // μΈν°μΉμ νμμ κ²½μ°, μ¬μ©λ νμμ λͺ¨λ  μμ±μ κ°μ§ μλ‘μ΄ νμμ΄ μμ±λ¨
  const someone: Person & Animal = {
    name: 'John Doe',
    species: 'Human',
    job: 'Student'
  };
  ```

  
