# CSS 🌈

> #### INDEX
>
> 1. [INTRO](#1.-INTRO)
> 2. [CSS 선택자](#2.-CSS-Selector)
> 3. [CSS 적용 규칙](#3.-CSS-적용-규칙)
> 4. [CSS 단위](#4.-CSS-단위)
> 5. [CSS 속성](#5.-CSS-속성)
> 6. [CSS Layout](#6.-CSS-Layout)



## 1. INTRO

> - Cascading Style Sheets
> - 스타일, 레이아웃 등을 통해 HTML이 문서(HTML)를 표시하는 방법을 지정하는 언어



#### 1. 기본 문법

```css
h1 {
    color: blue;
    font-size: 15px;
}
```

- 스타일을 지정할 요소를 지정하는 **선택자**와 함께 시작
- 중괄호 안에 스타일의 **속성**과 **값**을 쌍으로 하는 선언
- `선택자 {속성: 값;}`
  - 선택자: 스타일을 적용할 대상 (Selector)

    - HTML의 특정 element를 지정
  - 속성: 스타일의 종류(Property)
  - 값: 스타일의 값 (Value)



#### 2. 선언 방식

1. `Inline style`

   - 요소의 style 속성에 직접 스타일을 작성하는 방식

     ```html
     <div style="color: red;"></div>
     ```

     

2. 내부 참조 (`Embedding style`)

   - `<style></style>` 의 내용(Contents) 으로 스타일을 작성하는 방식

     ```html
     <head>
       ...
       <style>
         div {
           color: red;
         }
       </style>
     </head>
     ```

     

3. 외부 참조 (`Link style`)

   - `<link/>` 로 외부 CSS 문서를 가져와서 연결하는 방식 (병렬 연결 방식)

     ```html
     <head>
       ...
       <link rel="stylesheet" href="./main.css">
     </head>
     ```



4. @import 방식

   - CSS의 @import 규칙으로 CSS 문서 안에서 또 다른 CSS 문서를 가져와 연결하는 방식 (직렬 연결 방식)

   ```css
   @import url("./box.css");
   ```

   

## 2. CSS Selector

####  1. 기본 선택자

- 전체 선택자 (`*`) : 모든 요소를 선택
- 태그 선택자(`tag`) : 태그 이름으로 선택
- 클래스 선택자 (`.class`) : class 명으로 선택
- 아이디 선택자(`#id`) : id로 선택



#### 2. 복합 선택자

- 일치 선택자(`ABCXYZ`): 선택자 ABC와 XYZ를 동시에 만족하는 요소 선택 
  - ex. `span.title` > span 태그 중 클래스가 title인 요소 선택
    - cf. 특수문자가 없는 태그는 항상 맨 앞에 적기
- 자식 선택자(`ABC > XYZ`): 선택자 ABC의 자식 요소 중 XYZ를 만족하는 요소 선택
  - ex. `ul > .item` > ul 태그의 자식 요소 중 클래스가 item인 요소 선택
- 하위(후손) 선택자(`ABC XYZ`): 선택자 ABC의 하위 요소 중 XYZ를 만족하는 요소 선택 ('띄어쓰기'가 선택자의 기호)
  - ex. `div .title` > div 태그의 하위 요소 중 클래스가 title인 요소 선택
- 인접 형제 선택자(`ABC + XYZ`): 선택자 ABC의 다음 형제 요소 XYZ **하나**를 선택
  - ex. `.title + li` > .title 클래스 요소의 다음 형제 요소 중 가장 가까운 li 태그를 선택
- 일반 형제 선택자(`ABC ~ XYZ`): 선택자 ABC의 다음 형제 요소 XYZ를 모두 선택
  - ex. `.title ~ li` > .title 클래스 요소의 다음 형제 요소 중 li 태그를 모두 선택



#### 3. 가상 클래스 선택자

> 사용자가 특정 행동을 했을 때 동작하는 클래스

- ABC`:hover`: 선택자 ABC 요소에 <u>마우스 커서가 올라가 있는 동안</u> 선택
- ABC`:active`: 선택자 ABC 요소에 <u>마우스를 클릭하고 있는 동안</u> 선택 
- ABC`:focus`: 선택자 ABC 요소가 <u>포커스되면</u> 선택
  - 일반적으로 focus가 될 수 있는 요소는 HTML 대화형 콘텐츠에 해당
    - input, a, button, label, select 등
  - 대화형 콘텐츠 요소가 아니더라도 tabindex 속성을 사용한 요소도 focus 가능
    - tabindex 속성을 통해 포커스가 될 수 있는 요소를 만들 수 있는데, Tab 키를 사용해 포커스할 수 있는 순서를 지정하는 속성입니다. 순서(값)로 -1이 아닌 다른 값을 넣는 것은 논리적 흐름을 방해하기 때문에 권장하지는 않습니다. (ex. `<div tabindex="-1"></div>`)
- ABC`:first-child`: 선택자 ABC가 형제 요소 중 <u>첫째라면</u> 선택
- ABC`:last-child`: 선택자 ABC가 형제 요소 중 <u>막내라면</u> 선택
- ABC`:nth-child(n)`: 선택자 ABC가 형제 요소 중 <u>n번째라면</u> 선택
  - cf. 소괄호에 숫자와 `n`을 함께 쓰기도 하는데, **n은 0부터 시작**(Zero-based Numbering)
  - ABC`:nth-child(2n)` > 선택자 ABC 중 형제 요소의 짝수번째 요소를 선택(2번째, 4번째, 6번째, ...)
    - cf. 만약 소괄호에 `2n+1`을 넣으면 홀수번째 요소 선택
    - cf. `n+2`라면, 첫번째 요소만 빼고 선택
- cf. ABC`:not(XYZ)`: 선택자 XYZ가 아닌 ABC 요소 선택 (**부정 선택자**)



#### 4. 가상 요소 선택자

- `ABC::before`: 선택자 ABC 요소의 <u>내부 앞</u>에 내용(content)을 삽입

- `ABC::after`: 선택자 ABC 요소의 <u>내부 뒤</u>에 내용(content)을 삽입
  - 가상의 인라인(글자) 요소를 만들어서 선택한 요소 내부에 삽입하는 것!

```css
/* content 속성을 꼭 작성해야 동작 */
.box::before {
  content: "before";
}
.box::after {
  content: "after";
}

/* example */
.box::before {
  content: "";
  dispaly: block;
  width: 30px;
  height: 30px;
  background-color: blue;
}
```



#### 5. 속성 선택자

- `[ABC]`: 속성 ABC를 포함한 요소 선택

  ```css
  /* 
  [example]
  <input type="text" disabled>
  disabled라는 속성을 가진 요소를 선택할 때 사용
  */
  [disabled] {
    color: red;
  }
  ```

- `[ABC="XYZ"]`: 속성 ABC를 포함하고 값이 XYZ인 요소 선택

  ```css
  [type="password"] {
    color: blue;
  }
  ```

  

##  3. CSS 적용 규칙

####  1. Cascading Order

- 우선순위란, 같은 요소가 여러 선언의 대상이 된 경우, 어떤 선언의 CSS 속성을 우선 적용할지 결정하는 방법

  - 점수가 높은 선언이 우선하고, 같을 경우 가장 마지막에 해석된 선언(`선언 순서`)이 우선함

  ```html
  <div
    id="yellow"
    class="green"
    style="color: orange;"> <!-- 인라인 선언 (1000점) -->
    Hello world!
  </div>
  ```

  ```css
  div { color: red !impotant; } /* !important (inf 점) */
  #yellow { color: yellow; } /* ID선택자 (100점) */
  .green { color: green; } /* 클래스 선택자 (10점) */
  div { color: blue; } /* 태그 선택자 (1점) */
  * { color: darkblue; } /* 전체 선택자 (0점) */
  body { color: violet; }
  ```

  - cf. CSS 우선순위의 점수를 게산하는 것을 `명시도`라고 함
  - cf. `!important`를 사용하는 것은 `중요도`라고 함



####  2. 스타일 상속

1. 기본 상속
   - text 관련 요소(font, color, text-align)
   - opacity, visibility

2. 강제 상속

   - `inherit` 값을 활용해 해당 속성의 부모 값을 그대로 상속받도록 지정

   ```html
   <div class="parent">
     <div class="child"></div>
   </div>
   ```

   ```css
   .parent {
     width: 300px;
     height: 200px;
     background-color: orange;
   }
   
   .child {
     width: 100px;
     height: inherit;
     background-color: blue;
   }
   ```

   

## 4. CSS 단위

####  1. 크기 단위

- px(픽셀)
  - 모니터 해상도의 한 화소인 '픽셀'을 기준
  - 픽셀의 크기는 변하지 않기 때문에 고정적인 단위
- %
  - 가변적인 레이아웃에서 자주 사용되는 백분율 단위
- em
  - 요소에 지정된 사이즈에 상대적인 사이즈를 가지는 배수 단위
  - 상속의 영향을 받으며, 상황에 따라 각기 다른 값을 가질 수 있음
- rem
  - 최상위 요소인 `html(root em)`을 기준으로 하는 배수 단위 (기본값 `16px`)
  - 상속의 영향을 받지 않음
- Viewport 기준 단위
  - vw, vh, vmin, vmax



####  2. 색상 표현 단위

- 색상 키워드
  - red, blue, black과 같이 특정 색을 지칭
- RGB 색상
  - 16진수 표기법(#000000)이나 함수형 표기법(rgb(0, 0, 0))으로 사용
  - a는 alpha(투명도)가 추가
- HSL 색상
  - 색상, 채도, 명도를 통해 특정 색상을 표현
  - a는 alpha(투명도)가 추가



## 5. CSS 속성

#### 1. Box Model

> 웹 디자인은 contents를 담을 box model을 정의하고 CSS 속성을 통해 스타일(배경, 폰트와 텍스트 등)과 위치 및 정렬을 지정

- 모든 HTML 요소는 **box** 형태
- 하나의 박스는 네 부분(영역)으로 이루어 진다.
  1. Content: 글이나 이미지 등 요소의 실제 내용
  2. Padding: 테두리 안쪽의 **내부 여백**

  3. Border: 테두리 영역

  4. Margin: 테두리 바깥의 **외부 여백**



##### 1. 여백

- `margin`: 요소의 <u>외부 여백(공간)</u>을 지정하는 단축 속성 (default `0`)

  - 음수 값 사용 가능

  - `auto` 값 지정시, 가로(세로) 너비가 있는 요소의 가운데 정렬에 활용

  - `%`의 경우, 부모 요소의 가로 너비에 대한 비율로 지정

  - **마진 상쇄**: block의 top 및 bottom margin이 때로는 (결합되는 마진 중 크기가) 가장 큰 한 마진으로 결합(상쇄(collapsed))

  - 단축 속성

    1. margin: `top, right, bottom, left`;
    2. margin: `top, bottom`  `right, left`;
    3. margin: `top`  `right, left`  `bottom`;
    4. margin: `top`  `right`  `bottom`  `left`;

    

- `padding`: 요소의 <u>내부 여백(공간)</u>을 지정하는 단축 속성 (default `0`)

  - 패딩을 적용하면 요소의 크기가 증가
  - `%`의 경우, 부모 요소의 가로 너비에 대한 비율로 지정
  - 단축 속성
    1. padding: `top, right, bottom, left`;
    2. padding: `top, bottom`  `right, left`;
    3. padding: `top`  `right, left`  `bottom`;
    4. padding: `top`  `right`  `bottom`  `left`;



##### 2. 테두리

- `border`: 요소의 테두리 선을 지정하는 단축 속성 (default `medium none black`)
  - `border: border-width border-style border-color`
    - ex. `border: 1px solid black;`
  - 테두리의 width만큼 요소의 크기가 늘어남
  - 개별 속성
    - `border-width`: medium/thin/thick or 단위 (단축 속성 활용 가능)
    - `border-style`
      - **solid**, dotted, **dashed**, double, groove, ridge, inset, outset, none (단축 속성 활용 가능)
    - `border-color`
      - 색상을 지정하거나 `transparent(투명)` (단축 속성 활용 가능)
    - 방향 지정 시, `border-dir` or `border-dir-property`
- `border-radius`: 요소의 모서리를 둥글게 깎음 (default `0`)



##### 3. 크기 계산

- `box-sizing`: 요소의 <u>크기 계산 기준</u>을 지정 (default `content-box`)

  - `content-box`: 요소의 내용(content)으로 크기 계산

  - `border-box`: 요소의 내용 + padding + border로 크기 계산



##### 4. 넘침 제어

- `overflow`: 요소의 크기 이상으로 내용이 넘쳤을 때, 보여짐을 제어하는 단축 속성 (default `visible`)
  - `visible`: 넘친 내용을 그대로 보여줌
  - `hidden`: 넘친 내용을 잘라냄
  - `scroll`: 넘친 내용을 자르고, 무조건 스크롤바(x축, y축) 생성
  - `auto`: 넘친 내용이 있는 경우에만 잘라내고 스크롤바 생성
  - 개별 속성
    - `overflow-x`, `overflow-y`



#### 2. Display

- `display`: 요소의 화면 출력 특성
  - 기본 값은 각 요소에 이미 지정되어 있는 값
    - inline, block, inline-block, table 등
  - `flex`: 플렉스 박스 (1차원 레이아웃)
  - `grid`: 그리드 (2차원 레이아웃)
  - `none`
    - 해당 요소를 화면에 표시하지 않음 
      - 해당 요소의 공간도 사라짐
    - cf. `visibility: hidden;`, `opacity: 0;`
      - 해당 요소를 화면에 표시하지 않지만
      - 해당 요소의 **공간은 존재**



#### 3. Position

- `position`: 요소의 위치 지정 기준 (default `static`)

  - `relative`: 요소 <u>자신</u>을 기준
    - (위치를 바꿀 경우) 기존 자신의 위치는 비어 있는 것처럼 보이지만 실제 동작에는 해당 자리가 채워져 있음 

  - `absolute`: **위치 상** <u>부모</u> 요소를 기준
    - HTML 구조상 상위 요소 중 `position`이 있는 가장 가까운 요소 기준

  - `fixed`: <u>뷰포트</u>(브라우저)를 기준
    - 스크롤을 내리거나 올려도 화면에서 사라지지 않고 항상 같은 곳에 위치

  - `sticky`: <u>스크롤 영역</u> 기준
  - cf. position 속성의 값으로 `absolute`, `fixed`가 지정된 요소는 display 속성이 block으로 자동 변환

- `top`, `bottom`, `left`, `right` (default `auto`)



- cf. 요소 쌓임 순서(Stack order)

  - 어떤 요소가 사용자와 더 가깝게 있는지 결정

    1. 요소에 position 속성의 값이 있는 경우 위에 쌓임 (`static` 제외)
    2. 1번 조건이 같을 경우, z-index 속성의 숫자 값이 높을수록 위에 쌓임
    3. 2번까지 조건이 같을 경우, HTML의 다음 구조일수록 위에 쌓임

  - `z-index`: 요소의 쌓임 정도를 지정 (default `auto` == `사실상 0`)

  

#### 4. Text

- `font-style`: 글자의 기울기 (default `normal`)

- `font-weight`: 글자의 두께 (default `normal, 400`)

- `font-size`: 글자의 크기 (default `16px`)

- `font-family`: 글꼴(서체) 지정

  - `font-family: font1, "font 2", ... 글꼴 계열(필수 작성)`

    - 띄어쓰기 등 특수문자가 포함된 폰트 이름은 큰 따옴표로 묶기

    - 여러 개를 적을 경우, 앞에 명시된 글꼴 중 가능한 글꼴 사용

      - 모든 글꼴 후보가 다 사용 불가하면 명시된 글꼴 계열 중 사용 가능한 폰트 제공

    - cf. 글꼴 계열

      - `serif` 바탕체 계열
      - `sans-serif` 고딕체 계열
      - `monospace` 고정너비 글꼴 계열
      - `cursive` 필기체 계열
      - `fantasy` 장식 글꼴 계열

      

- `line-height`: 한 줄의 높이, 행간과 유사 (default `normal`)

  - 기본 값은 브라우저의 기본 정의를 사용하고, 초기화하면 `1`
  - 숫자의 경우, 요소의 <u>글꼴 크기의 배수</u>로 지정

  

- `color`: 글자의 색상 (default `rgb(0, 0, 0)`)
- `text-align`: 문자의 정렬 방식 (default `left`)
- `text-decoration`: 문자의 장식 (default `none`)
  - `underline`(밑줄), `overline`(윗줄), `line-through`(중앙선)

- `text-indent`: 문자 첫 줄의 들여쓰기 (default `0`)
  - 음수를 사용할 경우, 내어쓰기 적용



#### 5. Background

- `background-color`: 요소의 배경 색상 (default `transparent`)
- `background-image`: 요소의 배경 이미지 삽입 (default `none`)
  - `url("src")` 형식으로 이미지 경로 지정
  - 배경 색상과 함께 사용할 경우, 색상이 이미지 뒤에 위치
- `background-size`: 요소의 배경 이미지 크기 (default `auto`)
  - `auto`: 이미지의 실제 크기
  - `cover`: 비율을 유지하되, 요소의 더 넓은 너비에 맞춤
  - `contain`: 비율을 유지하되, 요소의 더 좁은 너비에 맞춤
  - 단위 지정 가능
- `background-repeat`: 요소의 배경 이미지 반복 (default `repeat`)
  - `repeat-x`, `repeat-y`, `no-repeat`
- `background-position`: 요소의 배경 이미지 위치 (default `0% 0%`)
  - 방향 (top, bottom, left, right, center) or 단위값 지정
  - `x축 y축` 위치 입력
- `background-attachment`: 요소의 배경 이미지 스크롤 특성 (default `scroll`)
  - `scroll`: 이미지가 요소를 따라 같이 스크롤
  - `fixed`: 이미지가 뷰포트에 고정, 스크롤 x  👉 요소는 올라가는데, 이미지는 고정
  - `local`: 요소 내 스크롤 시 이미지가 같이 스크롤



##### 6. Transition

- `transition: name duration timing-function delay;` (default `all 0 ease 0`)
  - 요소의 전환(시작과 끝) 효과를 지정하는 단축 속성
  - duration은 단축 속성의 필수 포함 속성
- `transition-property`: 전환 효과를 사용할 속성 이름을 지정 (default `all`)
- `transition-duration`: 전환 효과의 지속 시간 지정 (default `0`)
- `transition-timing-function`: 전환 효과의 타이밍(easing) 함수를 지정 (default `ease`)
  - `ease`: 느리게-빠르게-느리게 = `cubic-bezier(0.25, 0.1, 0.25, 1)`
  - `linear`: 일정하게 = `cubic-bezier(0, 0, 1, 1)`
  - `ease-in`: 느리게-빠르게 = `cubic-bezier(.42, 0, 1, 1)`
  - `ease-out`: 빠르게-느리게 = `cubic-bezier(0, 0, .58, 1)`
  - `ease-in-out`: 느리게-빠르게-느리게 = `cubic-bezier(.42, 0, .58, 1)`
  - `cubic-bezier(n, n, n, n)`: 자신만의 값을 정의
  - `steps(n)`: n번 분할된 애니메이션
  - cf. [Easing 함수 치트 시트](easing.net/ko)
- `transition-delay`: 전환 효과가 몇 초 뒤에 시작할지 결정 (default `0`)



##### 7. Transform

- `transform: 변환함수1 변환함수2 변환함수3 ...;`
  - 요소의 변환 효과 지정
  - 원근법, 이동, 크기, 회전, 기울임 등
- 2D 변환 함수
  - `translate(x, y)`, `translateX(x)`, `translateY(y)` 👉 이동
  - `scale(x, y)`, `scaleX(x)`, `scaleY(y)` 👉 크기
  - `rotate(degree)` 👉 회전 (각도)
  - `skew(x, y)`, `skewX(x)`, `skewY(y)` 👉 기울임
  - `matrix(n, n, n, n, n, n)` 👉 2차원 변환 효과
- 3D 변환 함수
  - `translateZ(z)`, `translate3d(x, y, z)`
  - `scaleZ(z)`, `scale3d(x, y, z)`
  - `rotateX(x)`, `rotateY(y)`, `rotateZ(z)`, `rotate3d(x, y, z, a)`
  - `perspective(n)` 👉 원근법(거리)
    - 원근법 합수는 제일 앞에 작성
- `perspective`: 하위 요소를 관찰하는 원근 거리를 지정
  - 속성과 함수의 차이점
    - `perspective: 600px;`
      - 관찰 대상의 부모에 적용
      - 기준점 설정: `perspective-origin`
    - `transform: perspective(600px);`
      - 관찰 대상에 적용
      - `transform-origin`
- `backface-visibility`: 3D 변환으로 회전된 요소의 뒷면 숨김 여부 (default `visible`)
  - `visible`, `hidden`



## 6. CSS Layout

> - 웹 페이지에 포함되는 요소들을 취합하고, 그것들이 어느 위치에 놓일 것인지를 제어하는 기술
> - Float / Flexbox / Grid



## 1. Float

> - Float된 이미지의 좌·우측 주변으로 텍스트를 둘러싸는 레이아웃을 위해 도입
> - 정상 흐름으로부터 벗어난 요소의 주위를 텍스트 및 인라인 요소가 감싸 좌·우측을 따라 배치되는 것을 지정



####  1. Float 속성

- `float: none` (default)
- `float: left` (해당 요소를 왼쪽으로 띄움)
- `float: right` (해당 요소를 오른쪽으로 띄움)



####  2. clearfix

- float 요소와 block 요소 간의 레이아웃이 깨지는 것을 방지하기 위한 기능

  ```css
  .clearfix::after {
    content: "";
    display: block;
    clear: both;
  }
  ```

  - float 속성을 적용한 요소의 **부모 요소**에 적용
  - 부모 태그 다음에 가상 요소로 내용이 빈 블럭을 만드는 것



## 2. Flexible Box

> - 요소 간의 공간 배분과 정렬 기능을 위한 1차원 레이아웃



####  1. Flexbox 기본 개념

- 요소
  - Flex Container (부모 요소)
    - 부모 요소에 `display: flex`를 작성
  - Flex Item (자식 요소)
- 축
  - main axis (메인 축)
  - cross axis (교차 축)



####  2. Flexbox 속성

- 배치 방향 설정
  - `flex-direction` (메인 축의 방향을 설정)
    1. `row` (default) →
    2. `row-reverse` ←
    3. `column` ↓
    4. `column-reverse` ↑



- 메인축 방향 정렬

  - `justify-content`
    - `flex-start`: 시작점으로 정렬
    - `flex-end`: 끝점으로 정렬
    - `center`: 가운데 정렬
    - `space-between`: 균등 정렬
    - `space-around`: 외부 여백 균등 정렬

  

- 교차축 방향 정렬

  - `align-items`
    - `flex-start` `flex-end` `center` `baseline` `stretch`
  - `align-self`
  - `align-content`

- 기타

  - `flex-wrap`: Flex Items 묶음(줄 바꿈) 여부 (default `nowrap`)
    - `nowrap`: 한 줄에 한 번에 표시 (자리가 부족하며 아이템 width가 찌그러짐)
    - `wrap`: 여러 줄로 묶음 (줄 바꿈 적용)
    - `wrap-reverse`
  - `flex-flow` : flex-direction 과 flex-wrap 의 shorthand
  - `flex-grow`: 아이템 증가 너비 비율 (default `0`)
    - 아이템이 차지하는 기본 영역을 제외하고 남는 공간을 나누는 기준
  - `flex-shrink`: 아이템 감소 너비 비율 (default `1`)
    - 아이템들이 차지하는 영역이 컨테이너 너비보다 넓을 때 적용
      - `0`을 적용하면 너비가 줄어들지 않음
  - `flex-basis`: 아이템 공간 배분 전 기본 너비 (default `auto`)
  - `order`: 플렉스 아이템 순서 (default `0`)
    - 작은 숫자일수록 앞으로 이동

  

