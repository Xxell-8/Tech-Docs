## TypeScript



## About

- 오픈소스 프로그래밍 언어
- 자바스크립트의 상위 집합으로 ECMA 스크립트의 최신 표준을 지원
- 정적인 언어로 컴파일 시간에 타입을 검사
  - 터미널에서 `tsc <파일명>` 명령을 통해 JS 파일로 컴파일 가능
- 장점
  - 강력한 타입으로 대규모 애플리케이션 개발에 용이₩
  - 유명한 자바스크립트 라이브러리와의 편리한 사용
  - 개발 도구에서의 강력한 지원



## 컴파일러

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
          // any type 지정 막기
          "noImplicitAny": true
      },
  }
  ```

  



