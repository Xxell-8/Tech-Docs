# HTML

> ## INDEX
>
> 1. [기본 HTML 구조](#1.-기본-구조)
> 2. [HTML 문서 구조화](#2.-HTML-문서-구조화)
> 3. [시맨틱 태그](3.-시맨틱-태그)



## Intro

> - Hyper Text Markup Language
> - 웹 페이지를 작성하기 위해 웹 콘텐츠의 의미와 구조를 정의하는 언어

- Web Standard

  - 월드 와이드 웹(WWW)을 구현하기 위해 따라야 할 표준 또는 규격
  - W3C(HTML5)과  **WHATWG**(HTML Living Standard)가 HTML 표준을 제정

  - [[NEWS] W3C와 WHATWG가 HTML과 DOM 규격을 단일 버전으로 개발하는 데 협력하는 합의안에 서명](https://www.w3.org/blog/2019/05/w3c-and-whatwg-to-work-together-to-advance-the-open-web-platform/)

  

- HTML 이란?
  - Hyper Text
    - 참조(하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
    - `http`, `html`
  - Markup Language
    - 특정 텍스트에 역할을 부여
    - ex. `h1` 태그를 붙여 의미론적으로 제목임을 마킹하는 것



## 1. 기본 구조

- DOM (Document Object Model)

  - 문서의 구조화된 표현을 제공

    - 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법을 제공 

      👉 문서 구조, 스타일, 내용 등을 변경할 수 있도록 돕는 것

  - 웹 페이지의 객체 지향 표현

    - 동일한 문서를 표현·저장·조작하는 방법을 제공



- 기본 구조

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Document</title>
  </head>
  <body>
    
  </body>
  </html>
  ```

  - `<!DOCTYPE html>` : 문서의 HTML 버전을 지정
  
    - DOCTYPE(DTD, Document Type Definition)은 마크업 언어에서 문서 형식을 정의하며, **웹 브라우저가 어떤 HTML 버전의 해석 방식으로 페이지를 이해하면 되는지를 알려주는 용도**
    
  - `<html>` : 문서의 **전체** 범위
  
    - HTML 문서의 최상위 요소로, 문서의 root를 의미
    - HTML 문서가 어디에서 시작하고, 어디에서 끝나는지 알려주는 역할
  
  - `<head>` : 문서의 **정보**를 나타내는 범위
  
    - 웹 브라우저가 해석해야 할 웹 페이지의 제목, 설명, 사용할 파일 위치, 스타일 같은 웹 페이지의 <u>보이지 않는 정보</u>를 작성하는 범위
  
    - 정보를 표시하는 태그
  
      - `title`: HTML 문서의 제목을 정의 > 웹 브라우저 탭에 표시됨
      - `meta`: HTML 문서의 제작자, 내용, 키워드 같은 여러 정보를 검색엔진이나 브라우저에 제공
  
      ```html
      <!-- charset 문자 인코딩 방식 지정 --> 
      <meta charset="UTF-8">
      <!-- name은 정보의 종류, content는 정보의 값 -->
      <meta name="author" content="xxell8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      ```
  
      - `link`: 외부 문서를 가져와 연결할 때 사용 (대부분 CSS 파일, 로고)
        - `rel`: 가져올 문서와 관계
        - `href`: 가져올 문서의 경로
      - `script`: 자바스크립트 파일을 가져오는 경우, 자바스크립트를 HTML 문서 안에서 작성하는 경우
      - `style`: 스타일을 HTML 문서 안에서 작성하는 경우에 사용
  
      
  
  - `<body>` : 문서의 **구조**를 나타내는 범위
  
    - 사용자 화면을 통해 보여지는 로고, 헤더, 푸터, 내비게이션, 메뉴, 버튼, 이미지 같은 웹 페이지의 <u>보여지는 구조</u>를 작성하는 범위
    - 브라우저 화면에 나타나는 정보로, 실제 내용에 해당되는 부분



- 요소 (Element)
  - HTML 요소는 시작 태그와 종료 태그, 그 사이에 위치한 콘텐츠(내용)로 구성
  - 태그는 콘텐츠(내용)를 감싸서 그 정보의 성격과 의미를 정의
    - ex. `<h1>contents</h1>`
  - 콘텐츠(내용)이 없는 태그들도 존재
    - `<br>`, `<hr>`, `<img>`, `<input>`, `<link>`, `<meta>`
  - 요소는 중첩(nested) 가능
    - HTML은 오류 없이 레이아웃이 깨져버리기 때문에 어떤 면에서는 오류 정보를 알려주는 프로그래밍보다 디버깅이 어려울 수 있음



- 속성 (Attribute)
  - 속성은 태그의 부가적인 정보
    - 요소에 실제론 나타내고 싶지 않지만 추가적인 내용(이미지 파일의 경로, 크기 등)을 담고 싶을 때 사용
    
    - 요소의 시작 태그에 위치해야 하며 **이름**과 **값**의 쌍
      - ex.  `<a href="https://www.mozilla.org/">Mozilla</a>`
      
    - 태그와 상관없이 사용 가능한 속성들(HTML Global Attribute, 전역 속성)도 존재
    
      - `title`: 요소의 정보나 설명을 지정 👉 해당 요소에 마우스 오버 시, 툴팁 형식으로 노출
    
      - `style`: 요소에 적용할 스타일(CSS)을 지정
    
      - `class`: 요소를 지칭하는 중복 가능한 이름
    
      - `id`: 요소를 지칭하는 고유한 이름
    
      - `data-이름`: 요소에 데이터를 지정
    
        ```html
        <div data-fruit-name="apple">사과</div>
        <div data-fruit-name="banana">바나나</div>
        ```
    
        ```js
        const els = document.querySelectorAll('div')
        els.forEach(el => {
          console.log(el.dataset.fruitName)
        })
        ```



## 2. HTML 문서 구조화

#### 1. Element 특성

| 인라인 요소                                                  | 블록 요소                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 글잘를 만들기 위한 요소들                                    | 상자(레이아웃)를 만들기 위한 요소들                          |
| - 포함한 콘텐츠의 크기만큼 공간을 차지<br />- 요소가 수평으로 쌓임 | - 부모 요소의 전체 크기만큼 공간을 차지<br />- 요소가 수직으로 쌓임 |
| - `width`, `height` 크기 지정 불가<br />- `margin`, `padding` Y축 크기 지정 불가<br />- 자식 요소로 블록 요소를 가질 수 없음 | - `width`, `height` 크기 지정 가능                           |



#### 2. 인라인(inline) 요소

- `<span>`: 특별한 의미가 없는 구분을 위한 요소
- `<img>`: 이미지를 삽입하는 요소 (Image)

- `<a>`: 다른/같은 페이지로 이동하는 하이퍼링크를 지정하는 요소 (anchor)
  - `href`: 링크 URL, `target`: 링크 URL의 표시(브라우저 탭) 위치
- `<br/>`: 줄바꿈 요소 (Break)
- `<label>`: 라벨 가능 요소(input)의 제목 
- `<b>`(bold) vs `<strong>`
  - 둘 다 볼드체를 만드는 기능인데, b는 그냥 굵게 / strong은 굵게 + 의미 강조(시맨틱 요소)
  - 스크린 리더가 읽을 때 strong을 강조해서 읽는다
- `<i>` vs `<em>`
  - 기울임체도 마찬가지로 em은 의미를 부여



#### 3. 블록(block) 요소

- `<div>`: 특별한 의미가 업슨 구분을 위한 요소 (Division)

- `<h1>`: 제목을 의미하는 요소 (Heading, 1 ~ 6)

- `<p>`: 문장을 의미하는 요소 (Paragraph)

- `<ul>` : 순서가 필요없는 목록의 집합을 의미 (Unordered List)

  - cf. `<ol>`

- `<li>`: 목록 내 각 항목 (List Item)



#### 4. 그 외의 요소

- `<input/>`: **인라인 블록 요소**로 사용자가 데이터를 입력하는 요소
  - 다양한 타입을 가지는 입력 데이터 필드
    - [[참고] input 유형](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input)
  - 공통 속성: `name`, `placeholder`, `required`, `autofocus` 등
  - 수평으로 쌓이되 사이즈, 여백 요소 지정이 자유롭게 가능



- `<table>`: **테이블 요소**로, 행과 열의 집합

  - `<tr>`: 행을 지정하는 요소 (Table Row)

  - `<td>`: 열을 지정하는 요소 (Table Data)

  - `<th>`: 테이블의 헤더 부분을 지정하는 요소

  - `<caption>`: 테이블 설명 요소

    

## 3. 시맨틱 태그

> - 의미론적 요소를 담은 태그 (HTML5)
> - 단순히 구역을 나누는 것에서 나아가, '의미'를 가지는 태그를 활용
> - [[참고] Semantics](https://developer.mozilla.org/ko/docs/Glossary/Semantics)



- 의미론적 마크업의 장점
  - 가독성 향상
    - 개발자가 의도한 요소의 의미가 명확히 드러나며,
    - 높은 가독성으로 전반적인 유지·보수에 도움
  - 접근성 향상
    - 검색엔진최적화(SEO)
      - 검색 엔진은 HTML 코드를 읽는데, 시맨틱 태그를 통해 마크업을 하면 콘텐츠의 이해도가 향상
      - 시각장애인을 위한 스크린리더 등 다양한 보조기술 향상에도 도움이 되며, 사용자 경험을 더 좋게 할 수 있음
- Semantic Tag
  - `header`: 문서 전체나 섹션의 헤더(머릿말)
  - `nav`: 내비게이션
  - `aside`: 사이드에 위치한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠
  - `section`: 문서의 일반적인 구분, 콘텐츠의 그룹을 표현
  - `article`: 문서, 페이지, 사이트 안에 독립적으로 구분
  - `footer`: 문서 전체나 섹션의 푸터(마지막 부분)

- Non-Semantic Tag
  - `div`, `span` 등



- **시맨틱 웹**
  - 웹에 존재하는 수많은 웹페이지들에 메타데이터를 부여
  - 기존의 단순한 데이터 집합이었던 웹페이지를 '의미'와 '관련성'을 가지는 거대한 데이터베이스로 구축하고자 하는 발상
