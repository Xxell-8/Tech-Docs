# Vue.js 🦄

> #### INDEX
>
> 1. [INTRO](#1.-INTRO)
> 2. [Vue.js](#2-Vue)
> 3. [Vue CLI](#3.-Vue-CLI)
> 4. [Vue Router](#4.-Vue-Router)
> 5. [Vuex](#5.-Vuex)



## 1. INTRO

### 1. SPA

>  Single Page Application (단일 페이지 애플리케이션)

- 현재 페이지를 동적으로 작성함으로써 사용자와 소통하는 웹 애플리케이션
- 단일 페이지로 구성되며 서버로부터 처음에만 페이지를 받아오고 이후에는 동적으로 DOM을 구성
  - 즉, 처음 페이지를 받은 이후에는 서버로부터 완전한 새로운 페이지를 불러오지 않고 현재 페이지를 동적으로 다시 작성
  - 연속되는 페이지 간의 **사용자 경험 향상**
  - 모바일 사용이 증가하고 있는 상황에서 트래픽의 감소와 속도, 사용성, 반응성 향상은 매우 중요한 이슈

- 등장 배경
  - 과거 웹 사이트는 요청에 따라 매번 새로운 페이지를 응답하는 방식
    - Multi Page Application (MPA)
  - 스마트폰 등장으로 모바일 최적화에 대한 필요성
    - 모바일 네이티브 앱과 같은 형태의 웹 페이지 필요
  - 이러한 문제를 해결하기 위해 Vue와 같은 프론트엔트 프레임워크 등장
    - CSR, SPA 등장
  - 1개의 웹 페이지에서 여러 동작이 이루어지며 모바일 앱과 비슷한 형태의 사용자 경험 제공



### 2. CSR

> Client Side Rendering

- 최초 요청 시 서버에서 빈 문서를 응답하고 이후 클라이언트에서 데이터를 요청해 데이터를 받아 DOM을 렌더링

- SSR보다 초기 전송되는 페이지 속도는 빠르지만, 서비스에서 필요한 데이터를 클라이언트(브라우저)에서 추가로 요청하여 재구성해야 하기 때문에 전체적인 페이지 완료 시점은 SSR보다 느림

- SPA가 사용하는 렌더링 방식

  | 장점                                                         | 단점                                          |
  | ------------------------------------------------------------ | --------------------------------------------- |
  | - 서버와 클라이언트 간의 트래픽 감소<br /> 👉 웹 애플리케이션에 필요한 모든 정적 리소스를 최초에 한 번 다운로드<br />- 사용자 경험 향상<br /> 👉 변경되는 부분만을 갱신 | - SEO (검색엔진 최적화) 문제가 발생할 수 있음 |

#### cf. SSR

>  Server Side Rendering

- 서버에서 사용자에게 보여줄 페이지를 모두 구성하여 사용자에게 페이지를 보여주는 방식

- 서버를 이용해서 페이지를 구성하기 때문에 클라이언트에서 구성하는 CSR보다 페이지를 구성하는 속도는 늦지만 사용자에게 보여주는 콘텐츠 구성이 완료되는 시점은 빨라짐

  | 장점                                                         | 단점                                                         |
  | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | - 초기 로딩 속도가 빠르기 때문에 사용자가 콘텐츠를 빨리 볼 수 있음<br />- SEO (검색엔진 최적화) 가능 | - 모든 요청에 새로고침이 되기 때문에 사용자 경험이 떨어짐<br /> 👉 상대적으로 요청 횟수가 많아져 서버 부담이 커짐 |



### 3. SEO

> Search Engine Optimization (검색 엔진 최적화)

- 웹 페이지 검색 엔진이 자료를 수집하고 순위를 매기는 방식에 맞게 웹페이지를 구성해서 검색 결과 상위에 노출될 수 있도록 하는 작업
- 인터넷 마케팅 방법 중 하나
- 구글 등장 이후 검색엔진이 콘텐츠의 신뢰도를 파악하는 기초 지표로 사용
  - 다른 웹 사이트에서 얼마나 인용되었나 반영
  - 타 사이트에 인용되는 횟수를 늘리는 방향으로 최적화

- 문제 대응
  - SPA 프레임워크는 SSR을 지원하는 SEO 대응 기술이 이미 존재
  - 추가적으로 프레임워크 사용 가능
    - Nuxt.js, Next.js



#### cf. SPA with SSR

- CSR과 SSR을 적절히 사용
  - Django에서 Axios를 활용한 좋아요/팔로우 로직의 경우
    - 대부분 서버에서 완성된 HTML을 제공하는 구조(SSR)
  - 특정 요소(좋아요/팔로우)만 AJAX를 활용한 비동기요청으로 필요한 데이터를 클라이언트에서 서버로 직접 요청을 보내 받아오고 JS를 활용해 DOM 조작 (CSR)



#### 4. SFC

> Single File Component

- Vue의 컴포넌트 기반 개발의 핵심 특징

- 하나의 컴포넌트는 .vue라는 하나의 파일 안에서 작성되는 코드의 결과물

- 화면의 특정 영역에 대한 HTML, CSS, JavaScript 코드를 하나의 파일(.vue)에서 관리

- 즉, .vue 확장자를 가진 싱글 파일 컴포넌트를 통해 개발하는 방식

  - Vue 컴포넌트 === Vue 인스턴스 === .vue 파일

  

##### cf. Component

- 기본 HTML 엘리먼트를 확장하여 재사용 가능한 코드를 캡슐화하는데 도움을 줌
- CS에서는 다시 사용할 수 있는 범용성을 위해 개발된 소프트웨어 구성 요소를 의미
- 즉, 컴포넌트 개발을 함에 있어 유지보수를 쉽게 만들어줄 뿐만 아니라, 재사용성의 측면에서도 매우 강력한 기능을 제공



## 2. [Vue](https://v3.ko.vuejs.org/guide/introduction.html)

> - 사용자 인터페이스를 만들기 위한 진보적인 프레임워크
> - 현대적인 tool과 다양한 라이브러리를 통해 SPA(Single Page Aplication)를 완벽하게 지원
> - Evan You에 의해 발표
>   - 구글 Angular 보다 가볍고, 간편하게 사용할 수 있는 프레임워크를 만들기 위해 개발



### 1. Why Vue.js?

- 현대 웹 페이지는 페이지 규모가 계속해서 커지고 있으며, 그만큼 사용하는 데이터도 늘어나고 사용자와의 상호작용도 많이 이루어짐
- 결국 Vanilla JS 만으로는 관리하기 어려움

  - '모든 요소'를 선택해서 '이벤트'를 등록하고 값을 변경해야 하기 때문!

  - Vue.js를 활용할 경우,
    - DOM과 Data가 연결되어 있으면,
      - Data를 변경하면 이에 연결된 DOM은 알아서 변경
      - 즉, Data에 대한 관리가 중요



### 2. MVVM Pattern

- 애플리케이션 로직을 UI로부터 분리하기 위해 설계된 디자인 패턴

  ![MVVMPattern](assets/3-2.Vuejs.assets/MVVMPattern.png)



1. Model

   - **JS Object**

     - Vue Instance 내부에서 data로 사용되며, 이 값이 바뀌면 View(DOM)가 반응

       

2. View

   - DOM(HTML)

     - Data의 변화에 따라 바뀌는 대상

     

3. View Model

   - 모든 Vue Instance
     - View와 Model 사이에서 Data와 DOM에 관련된 모든 일을 처리
     - ViewModel을 활용해 Data를 얼마만큼 잘 처리해서 보여줄지(DOM) 고민



#### cf. 코드 작성 순서

- Django

  - 데이터 흐름에 따라 작성
  - url 👉 views 👉 template

  

- Vue.js

  - Data에 따라 DOM이 변경
    - Data 로직 작성 👉 DOM 작성



### 3. Basic Syntax

#### 1. Vue Instance

- Vue 인스턴스 생성 시, Options 객체를 전달

  - 여러 Options을 사용하여 원하는 동작 구현

    | Option    | Descriptions                                                 |
    | --------- | ------------------------------------------------------------ |
    | `el`      | - Vue 인스턴스에 연결(마운트)할 기존 DOM 엘리먼트 필요<br />- CSS 선택자 문자열 혹은 HTMLElenment로 작성<br />- new를 이용한 인스턴스 생성에만 사용 |
    | `data`    | - Vue 인스턴스의 데이터 객체로, Vue 앱의 상태 데이터를 정의<br />- template에서 interpolation을 통해 접근<br />- `v-bind`, `v-on` 등 디렉티브에서도 사용 <br />- Vue 객체 내 다른 함수에서 this 키워드를 통해 접근 가능<br /> 👉 data에서 화살표 함수 사용 금지<br />   👉 부모 컨텍스트를 바인딩하여 `this`가 Vue 인스턴스를 가리키지 않을 수 있음 |
    | `methods` | - Vue 인스턴스에 추가할 메서드<br />- template에서 interpolation을 통해 접근<br />- `v-on`과 같은 디렉티브에서도 사용 가능<br />- Vue 객체 내 다른 함수에서 this 키워드를 통해 접근 가능<br /> 👉 data에서 화살표 함수 사용 금지<br />   👉 `this` 키워드가 제대로 동작하지 않음 |

- Vue Instance === Vue Component



##### cf. `this`

- Vue 함수 객체 내에서 vue 인스턴스를 가리킴
- 단, JS 함수에서의 this 키워드는 다른 언어와 조금 다르게 동작
- 화살표 함수를 사용하면 안되는 경우
  - data
  - method 정의



#### 2. Template Syntax

> - 렌더링된 DOM을 기본 Vue 인스턴스의 데이터에 선언적으로 바인딩할 수 있는 HTML 기반 템플릿 구문을 사용
>   - Interpolation
>   - Directive



##### 1. Interpolation

1. Text
   - `<span>제목: {{ title }}</span>`
2. Raw HTML

   - `<span v-html="rawHtml"></span>`
3. Attributes
   - `<div v-bind:id="userId"></div>`
4. JS 표현식
   - `{{ num + 1 }}`
   - `{{ overview.split('').reverse().join('') }}`



##### 2. Directive

- v- 접두사가 있는 특수 속성
- 표현식의 값이 변경될 때 반응적으로 DOM에 적용하는 역할
- 전달인자
  - `:` (콜론)을 통해 전달인자를 받을 수 있음
- 수식어
  - `.` 으로 표시되는 특수 접미사
  - 디렉티브를 특별한 방법으로 바인딩해야 함을 나타냄



| Directive | Description                                                  |
| --------- | ------------------------------------------------------------ |
| `v-text`  | - 엘리먼트의 textContent를 업데이트<br />- 내부적으로 interpolation 문법이 v-text로 컴파일 됨<br />- `<p v-text="title"></p>` |
| `v-html`  | - 엘리먼트의 innerHTML을 업데이트  👉 **XSS 공격**에 취약<br />- 임의의 사용자로부터 입력 받은 내용은 v-html **절대 사용 금지** |
| `v-show`  | - 조건부 렌더링 중 하나<br />- 엘리먼트는 항상 렌더링되고 DOM에 남아 있음<br />- 단순히 엘리먼트에 display CSS 속성(`display: none;`)을 토글<br />- Expensive initial load, cheap toggle<br />  👉 토글이 자주 일어나는 요소일 경우 활용 |
| `v-if`    | - 조건부 렌더링 중 하나로, 조건에 따라 블록을 렌더링<br />- 디렉티브 표현식이 true일 때만 렌더링<br />- 엘리먼트 및 포함된 디렉티브는 토글하는 동안 삭제되고 다시 작성됨<br />- `v-else-if`, `v-else` 도 사용 가능<br />- Cheap initial load, Expensive toggle<br />  👉 자주 변경되지 않을 경우 활용 |
| `v-for`   | - 원본데이터를 기반으로 엘리먼트 또는 템플릿 블록을 여러 번 렌더링<br />- `item in items` 구문 사용 <br />- item 위치의 변수를 각 요소에서 사용할 수 있음<br /> 👉 v-for 사용시 반드시 key 속성을 각 요소에 작성 <br />- `v-if`와 `v-for`를 동시에 사용할 경우, `v-for`의 우선순위가 더 높음<br />  👉 `v-if`와 `v-for`를 동시에 사용하지 말 것!<br />     ✅ [스타일 가이드](https://kr.vuejs.org/v2/style-guide/#v-if%EC%99%80-v-for%EB%A5%BC-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EB%A7%88%EC%84%B8%EC%9A%94-%ED%95%84%EC%88%98) |
| `v-on`    | - 엘리먼트에 이벤트 리스너 연결<br />- 이벤트 유형은 전달인자로 표시<br />- 특정 이벤트가 발생했을 때, 주어진 코드가 실행<br />- `v-on:click` 👉 `@click` |
| `v-bind`  | - HTML 요소의 속성에 Vue의 상태 데이터를 값으로 할당<br />- Object 형태로 사용하면 vaue가 true인 key가 class 바인딩 값으로 할당<br />- `v-bind:href` 👉 `:href` |
| `v-model` | - HTML form 요소의 값과 data를 양방향 바인딩 수식어 <br />- [`.lazy`](https://kr.vuejs.org/v2/guide/forms.html#lazy) : `input`대신 `change` 이벤트 반영 <br />- [`.number`](https://kr.vuejs.org/v2/guide/forms.html#number) : 문자열을 숫자로 변경<br />- [`.trim`](https://kr.vuejs.org/v2/guide/forms.html#trim) : 입력에 대한 trim 적용 |



#### 3. Computed

- 데이터를 기반으로 하는 계산된 속성
- 함수의 형태로 정의하지만 함수가 아닌 함수의 반환 값이 바인딩
- 종속된 대상을 따라 저장(캐싱)되며, 종속된 대상이 변경될 때만 함수 실행

- 즉, Date.now() 처럼 아무 곳에도 의존하지 않는 computed 속성의 경우 절대로 업데이트되지 않음
- 반드시 반환 값이 있어야 함



##### cf. watch

- 데이터를 감시

- 데이터에 변화가 일어났을 때 실행되는 함수

  | computed                                                     | watch                                                        |
  | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | 특정 값이 변동하면 특정 값을 새로 계산해서 보여준다.         | 특정 값이 변동하면 다른 작업을 실행한다.                     |
  | - 특정 데이터를 직접적으로 사용/가공하여 다른 값으로 만들 때 사용<br />- computed 속성은 계산해야 하는 목표 데이터를 정의하는 방식으로 소프트웨어 공학에서 이야기하는 ‘**선언형** 프로그래밍’ 방식 | - 특정 데이터의 변화 상황에 맞춰 다른 data 등이 바뀌어야 할 때 주로 사용<br />- watch 속성은 감시할 데이터를 지정하고 그 데이터가 바뀌면 이런 함수를 실행하라는 방식으로 소프트웨어 공학에서 이야기하는 ‘**명령형** 프로그래밍’ 방식 |
  |                                                              |                                                              |



##### cf. computed & methods

- computed 속성 대신 methods에 함수를 정의할 수 있음
  - 최종 결과에 대해 두 가지 접근 방식은 서로 동일
- 단, computed 속성은 종속 대상을 따라 저장(캐싱) 됨
  - 종속된 대상이 변경되지 않는 한 computed에 작성된 함수를 여러 번 호출해도 계산을 다시 하지 않고 계산되어 있던 결과를 반환
  - 이에 비해 methods를 호출하면 렌더링을 다시 할 때마다 항상 함수를 실행



#### 4. filters

- 텍스트 형식화를 적용할 수 있는 필터
- interpolation 혹은 v-bind를 이용할 때 사용 가능
- 필터는 자바스크립트 표현식 마지막에 `|`와 함께 추가
- 체이닝 가능



### 4. Lifecycle Hooks

- 각 Vue 인스턴스는 생성될 때 일련의 초기화 단계를 거침

  - 예를 들어 데이터 관찰 설정이 필요한 경우, 인스턴스를 DOM에 마운트하는 경우, 그리고 데이터가 변경되어 DOM을 업데이트하는 경우 등

- 그 과정에서 사용자 정의 로직을 실행할 수 있는 라이프 사이클 훅도 호출됨

  ![lifecycle](assets/3-2.Vuejs.assets/lifecycle.png)

  



## 3. Vue CLI

>  Vue.js 개발을 위한 표준 도구
>
>  - 프로젝트의 구성을 도와주는 역할을 하며, Vue 개발 생태계에서 표준 tool 기준을 목표로 함
>  - 확장 플러그인, GUI, ES6 구성 요소 제공 등 다양한 tool 제공



#### 1. Node.js

- 자바스크립트를 브라우저가 아닌 환경에서도 구동할 수 있도록 하는 자바스크립트 런타임 환경
  - 브라우저 밖을 벗어날 수 없던 자바스크립트 언어의 태생적 한계를 해결
- Chrome V8 엔진을 제공하여 여러 OS 환경에서 실행할 수 있는 환경을 제공
- 즉, 단순히 브라우저만 조작할 수 있던 자바스크립트를 SSR에서도 사용가능하도록 함
  - 2009년 Ryan Dahl 발표



#### 2. NPM (Node Package Manage)

- 자바스크립트 언어를 위한 패키지 관리자
  - pip와 마찬가지로 다양한 의존성 패키지를 관리
- Node.js의 기본 패키지 관리자



#### 3. Babel

> JavaScript Transcompiler

- 자바스크립트의 신버전 코드를 구버전으로 번역/변환해주는 도구
- 자바스크립트 역사에 있어 파편화와 표준화의 영향으로 작성된 코드의 스펙트럼이 매우 다양
  - 최신 문법을 사용해도 브라우저의 버전별로 동작하지 않는 상황 발생
  - 같은 의미의 다른 코드를 작성하는 등의 대응이 필요해졌고 이러한 문제 해결을 위한 도구
- 원시 코드(최신 버전)를 목적 코드(구 버전)으로 옮기는 번역기가 등장하면서 특정 브라우저에서 동작하지 않는 상황에 대해 ㅋ크게 고민하지 않을 수 있음



#### 4. Webpack

- static module bundler
- 모듈 간의 의존성 문제를 해결하기 위한 도구



#### cf. Module

- 모듈은 단지 파일 하나를 의미
- 등장 배경
  - 브라우저만 조작할 수 있었던 시기의 자바스크립트는 모듈 관련 문법 없이 사용되어짐
  - 하지만 자바스크립트와 애플리케이션이 복잡해지고 크기가 커지자 전역 스코프를 공유하는 형태의 기존 개발 방식의 한계가 드러남
  - 라이브러리를 만들어 필요한 모듈을 언제든지 불러오거나 코드를 모듈 단위로 작성하는 등의 다양한 시도가 이루어짐
- 모듈 시스템이 2015년 표준으로 등재되며, 현재 대부분의 브라우저와 Node.js가 모듈 시스템 지원

- **Module 의존성 문제**
  - 모듈의 수가 많아지고 라이브러리 혹은 모듈 간의 의존성(연결성)이 깊어지면서 특정한 곳에서 발생한 문제가 어떤 모듈 간의 문제인지 파악하기 어려워짐
  - Webpack은 모듈 간의 의존성 문제를 해결하기 위해 존재하는 도구



#### cf. Bundler

- 모듈 의존성 문제를 해결해주는 작업이 Bundling이고 이러한 일을 해주는 도구가 Bundler
  - Webpack은 다양한 Bundler 중 하나
- 모듈들을 하나로 묶어주고 묶인 파일은 하나(혹은 여러 개)로 만들어짐
- Bundling된 결과물은 더 이상 서-순에 영향받지 않고 동작
- Bundling 과정에서 문제가 해결되지 않으면 최종 결과물을 만들어낼 수 없기 때문에 유지·보수 측면에서도 매우 편리해짐
- Vue CLI는 Babel, Webpack에 대한 초기 설정이 자동으로 되어 있음



## 4. Vue Router

>  vue.js의 공식 라우터
>
>  - 중첩된 라우트/뷰 매핑 모듈화 된, 컴포넌트 기반의 라우터 설정 등 SPA 상에서 라우팅을 쉽게 개발할 수 있는 기능 제공



#### 1. router 작성

- `router-link`

  - index.js 파일에 정의한 경로에 등록한 특정한 컴포넌트와 매핑
  - HTML5 히스토리 모드에서, router-link는 클릭 이벤트를 차단하여 브라우저가 페이지를 다시 로드하지 않도록 함
  - a 태그지만 우리가 알고 있는 GET 요청을 보내는 a태그와 다르게, 기본 GET 요청을 보내는 이벤트를 제거한 형태로 구성

  

- `router-view`

  - 실제 컴포넌트가 DOM에 부착되어 보이는 자리를 의미
  - router-link를 클릭하면 해당 경로와 연결되어 있는 index.js에 정의한 컴포넌트가 위치



- cf. components vs views
  - 컴포넌트 구조화 방식
    - `App.vue`
      - 최상위 컴포넌트
    - `views/`
      - **router(index.js)에 매핑되는 컴포넌트**를 모아두는 폴더
    - `components/`
      - router에 매핑된 **컴포넌트 내부에 작성하는 컴포넌트**를 모아두는 폴더



- cf. History mode
  - HTML history API를 사용해서 router를 구현
  - 브라우저의 히스토리는 남기지만 실제 페이지는 이동하지 않는 기능을 지원



#### 2. Vue Router가 필요한 이유

1. SPA 등장 이전

   - 서버가 모든 라우팅을 통제 👉 요청 경로에 맞는 HTML 제공

2. SPA 등장 이후

   - 서버는 index.html 하나만 제공

   - 이후 모든 처리는 HTML 위에서 JS 코드를 활용해 진행

     👉 요청에 대한 처리를 더 이상 서버가 하지 않음

3. 라우팅 처리 차이

   - SSR
     - 라우팅에 대한 결정권을 서버가 가짐
   - CSR
     - 클라이언트는 더이상 서버로요청을 보내지 않고 응답받은 HTML 문서 안에서 주소가 변경되면 특정 주소에 맞는 컴포넌트를 렌더링
     - 라우팅에 대한 결정권을 클라이언트가 가짐
   - Vue Router는 라우팅의 결정권을 가진 vue.js에서 라우팅을 편리하게 할 수 있는 tool을 제공해주는 라이브러리



## 5. Vuex

> - statement management pattern + library for vue.js
>   - 상태 관리 패턴 + 라이브러리
> - 상태를 전역 저장소로 관리할 수 있도록 지원하는 라이브러리
>   - state가 예측 가능한 방식으로만 변경될 수 있도록 보장하는 규칙 설정
>   - 애플리케이션의 모든 컴포넌트에 대한 중앙 집중식 저장소 역할
> - Vue의 공식 devtools와 통합되어 기타 고급 기능 제공



### 1. Pass Props & Emit Events

- 컴포넌트는 부모-자식 관계에서 가장 일반적으로 함께 사용하기 위함
- 부모는 자식에게 데이터를 전달(Pass props)하며, 자식은 자신에게 일어난 일을 부모에게 알림(Emit event)
  - 부모와 자식이 명확하게 정의된 인터페이스를 통해 격리된 상태로 유지할 수 있음
- `props는 아래로, events는 위로`
  - 부모는 props를 통해 자식에게 데이터 전달, 자식은 events를 통해 메시지를 전달



##### 1. 단방향 데이터 흐름

- 모든 props는 하위속성과 상위속성의 단방향 바인딩을 형성
- 부모 속성이 변경되면 자식 속성에 전달되지만, 반대는 안 됨
  - 자식 요소가 의도치 않게 부모 요소의 상태를 변경함으로써 앱의 데이터 흐름을 이해하기 어렵게 만드는 일을 막기 위함
- 부모 컴포넌트가 업데이트될 때마다 자식 요소의 모든 prop들이 최신 값으로 업데이트됨



##### 2. Props

- props는 상위 컴포넌트의 정보를 전달하기 위한 사용자 지정 특성

- 하위 컴포넌트는 props 옵션을 사용하여 수신하는 props를 명시적으로 선언해야 함

- 즉, data는 props 옵션을 통해 하위 컴포넌트로 전달

- 이름 컨벤션

  - in HTML

    - kebab-case

  - in 

    - camelCase

    

##### 3. Emit event

- $emit(event)

  - 현재 인스턴스에서 이벤트를 트리거
  - 추가 인자는 리스너의 콜백 함수로 전달

- 부모 컴포넌트는 자식 컴포넌트가 사용되는 템플릿에서 `v-on`을 사용하여 자식 컴포넌트가 보낸 이벤트를 청취

- event 이름

  - 컴포넌트 및 props와 달리, 이벤트는 자동 대소문자 변환을 제공하지 않음

  - HTML의 대소문자 구분을 위해 DOM 템플릿의 v-on 이벤트 리스너는 항상 자동으로 소문자 변환되기 때문에 `v-on:customEvent`는 자동으로 `v-on:customevent`로 변환

    - 때문에 이벤트 이름에는 kebab-case 사용 권장

    

### 2. Vuex Core Concept

- **단방향 데이터 흐름**
  - 상태(state)는 앱을 작동하는 원본 소스 (data)
  - 뷰(view)는 상태의 선언적 매핑
  - 액션(action)은 뷰에서 사용자 입력에 대해 반응적으로 상태를 바꾸는 방법(methods)

- 단방향 데이터 흐름의 단점

  - 공통의 상태를 공유하는 여러 컴포넌트가 있는 경우 빠르게 복잡해짐

- 상태 관리 패턴
  - 컴포넌트의 공유된 상태를 추출하고 이를 전역에서 관리하도록 함
  - 컴포넌트는 커다란 뷰가 되며 모든 컴포넌트는 트리에 상관없이 state에 접근하거나 동작을 트리거할 수 있음
  - 상태 관리 및 특정 규칙 적용과 관련된 개념을 정의하고 분리함으로써 코드의 구조와 유지 관리 기능 향상



### 3. Vuex 구성 요소

#### 1. State

- 중앙에서 관리하는 모든 상태 정보(data)
- Mutations에 정의된 method에 의해 변경
- 여러 컴포넌트 내부에 있는 특정 state를 중앙에서 관리
  - Vuex Store에서 컴포넌트에서 사용하는 state를 한 눈에 파악 가능
  - state가 변화하면 해당 state를 공유하는 컴포넌트의 DOM은 자동 렌더링
- 컴포넌트는 Vuex Store에서 state 정보를 가져와 사용



#### 2. Actions

- 컴포넌트에서 `dispatch()` 메서드에 의해 호출
- Backend API와 통신하여 Data Fetching 등의 작업을 수행
  - 동기적 작업 뿐만 아니라 **비동기적 작업 포함 가능**
- 항상 `context`가 인자로 넘어옴
  - store.js 파일 내에 있는 모든 요소에 접근해서 속성 접근 + 메서드 호출 가능
  - 단, (가능하지만) state를 직접 변경하지 않음
- mutations에 정의된 메서드를 `commit` 메서드로 호출
- state는 mutations 메서드를 통해서만 조작
  - 명확한 역할 분담을 통해 서비스 규모가 커져도 state를 올바르게 관리하기 위함



#### 3. Mutations

- Actions에서 `commit()` 메서드에 의해 호출
- 비동기적으로 동작하면 state가 변화하는 시점이 달라질 수 있기 때문에 **동기적 코드만 작성**
- mutations에 정의하는 메서드의 첫 번째 인자로 `state`가 넘어옴



#### 4. Getters

- state를 변경하지 않고 활용하여 계산을 수행 (computed와 유사)
  - 실제 계산된 값을 사용하는 것처럼 getters는 저장소의 상태(state)를 기준으로 계산
- getters 자체는 state를 변경하지 않음
  - state를 특정한 조건에 따라 구분(계산)



### 4. 바인딩 헬퍼

- `mapState`, `mapGetters`, `mapActions`, `mapMutations`
- Spread Operator(`...`)를 활용해 각 프로퍼티를 가져와 필요한 부분만 사용
