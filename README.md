# BaeminMart-Clone

> 🛒 HTML/CSS로만 배민상회 만들어보기

<br/>

## 미리보기

![배민상회_1차완성](/image/배민상회_1차완성.png)

<br/>

## 배운 것 & 다시 알게된 것

### 태그별 용도 정리

#### `<div>`

- 블록 레벨 요소로 **컨테이너 역할**
- 주로 **구획**을 만들거나 스타일을 적용하기 위해 사용
- 여러 요소들을 묶어서 **그룹화**하거나 스타일을 지정할 때 주로 사용
- **줄 바꿈**을 일으키므로 새로운 줄에서 시작

#### `<span>`

- **인라인 요소**로, **특정 부분에 스타일**을 적용하기 위해 사용
- 텍스트나 인라인 요소들을 감싸서 스타일을 지정할 때 사용
- **줄 바꿈을 일으키지 않고** 텍스트 내에서 **같은 줄에 표시**

#### `<p>`

- **블록 레벨 요소**로, **단락**을 나타내는 데 사용
- **문단의 시작과 끝을 지정**하는 역할
- 위 아래로 간격을 띄우며, 기본적으로 브라우저에 의해 자동적으로 여백이 주어짐

#### 정리하자면

- `<div>` : 섹션을 나누는 역할 → 여러 개의 요소를 그룹화해 레이아웃 구성
- `<span>` : 더 작은 범위에서 사용 → 텍스트 일부를 스타일링
- `<p>` : 텍스트의 구조적인 의미나 줄 바꿈 필요 시 → 제품 정보나 설명 등

### 이미지 가운데 정렬하는 방법

```html
display: block;
margin-left: auto;
margin-right: auto
```

### 문장 안의 일부 글자만 스타일링 하는 방법

```html
<p>이건<span style="color: yellow;">일부</span>문장</p>
```

- span 태그는 `display : inline` 이라는 스타일 속성을 내포하고 있기에
- `display : inline`을 가지고 있는 요소는 폭, 높이 등을 단독으로 결정할 수 없음
- 폭, 높이를 주고싶으면 이를 감싸고 있는 `<p>`에 주기

### selector 사용법

- 만약 스타일이 겹칠 경우, html의 style > id > class > tag selector 순으로 적용됨

```css
/* class selector */
.title {
  text-align: center;
}

/* tag selector */
p {
  text-align: center;
}

/* id selector */
#title {
  text-align: center;
}

/* 공백을 두어 부모 태그 안의 모든 자식들 선택 가능 */
.nav li {
  display: inline-block;
}

/* 꺽쇠를 사용해 바로 밑에 있는 자식만 선택 가능 */
.nav > li {
  display: inline-block;
}

/* 더욱 상세히 선택하고 싶다면
하지만 4개 이상 여러개 쓰면 직관적이지 X, 차라리 중간에 class 하나 더 만들기*/
.nav > li > span {
  color: red;
}
```

### display: block이 내장되어 있는 div

- 모든 `<div>`, `<p>`, `<h1>`, `<li>` 등은 `display : block` 속성을 주지 않아도 기본적으로 내장되어 있음. 그래서 `<div>`, `<p>`를 그냥 사용하면 한 행을 전부 차지하게 됨.
- 이렇게 하고 싶지 않다면 display 속성을 `inline`, `inline-block`, `flex` 등으로 주면 됨.

### 일부 스타일은 inherit(상속) 됨

- `font-size`, `color`, `font-family`, `text-align` 속성은 부모태그에 적용하면 안에 있던 자식 태그들에까지 모두 상속됨

### 요소를 공중에 띄워 왼쪽/오른쪽 정렬하는 float 속성

```css
/* box 2개를 만들어 각각 왼쪽으로 정렬 */
.left-box {
  width : 100px; 
  height : 100px;
  float : left;
}

.right-box {
  width : 100px; 
  height : 100px;
  float : left;
}

.footer {
  clear : both
}
```

- 다만, `float`를 쓰면 요소를 붕 띄우다보니 그 다음에 오는 HTML 요소들이 제자리를 찾지 못하기에 항상 `clear` 속성이 필요함
- 더불어, `float`로 가로 정렬 시, float 박스들을 싸매는 하나의 큰 div 박스를 만들고 width를 지정해 주는게 좋음. (그래야 모바일에서도 흘러넘치지 않고 잘 보임)
- `float : none`도 추가해 주는게 추후 생길 버그 예방 차원에서도 좋음.

### 텍스트 수평 & 수직 가운데 정렬

```css
.class {
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

### class 2개 이상 부여하려면

```css
/* class명을 띄어쓰기 후 연달아 작성 */
<ul class="navbar content">
```

### a 태그 링크 설정

```html
<!-- 아무 링크 없이 임시로 넣어두려면 -->
<a href="#" class="link">링크</a>
```

```css
.navbar a {
  font-size: 20px;
  text-decoration: none;
  color: inherit; /* 현재 요소에서 상속된 색상 사용 */
}

.navbar a:hover {
  text-decoration: none; /* 호버 시 밑줄 없애기 */
  color: inherit; /* 호버 시 색상 변경하지 않음 */
}

/* 클릭 시 색상 변경을 없애기 위해 active 스타일을 재정의 */
.navbar a:active {
  color: inherit;
}
```

### position

- 속성 값 4가지

  ```css
  .box {
    position : static; /* 기준: 없음 (좌표적용 불가) */
    position : relative; /* 기준: 내 원래 위치 */
    position : absolute; /* 기준: (position : relative를 가지고 있는) 내 부모 */
    position : fixed; /* 기준: 브라우저 창 (viewport) */
  }
  ```

- position : absolute 를 적용한 요소 가운데 정렬

  ```css
  .button {
    position : absolute; 
    left : 0;
    right : 0; 
    margin-left : auto;
    margin-right : auto;
    width : 적절히
  }
  ```

### 박스의 폭을 border까지 설정해주고 싶을 때

```css
.box {
  box-sizing : border-box; /* 박스의 폭은 border까지 포함 */
  box-sizing : content-box; /* 박스의 폭은 padding 안쪽 */
}

.div {
  box-sizing : border-box; /* 보통 css파일 맨 위에 써놓고 시작하면 좋음 */
}
```

### CSS 파일 작성시 기본으로 쓰면 좋을 속성들

혹은 [CSS normalize](https://github.com/necolas/normalize.css/blob/master/normalize.css)
로 브라우저간 통일된 스타일을 주어도 좋음. 다운 받아서 `<link>` 태그로 첨부하기

```css
div {
  box-sizing : border-box;
}

body {
  margin : 0;
}

html {
  line-height : 1;
}
```

### HTML 속성으로 CSS 셀렉터 사용하기

```css
/* input의 type속성이 email인 요소만 찾아서 스타일을 주기 */
input[type=email] {
  color : grey;
}
```

### label 태그와 for 속성

```html
<!-- input 태그의 id와 label 태그의 for 속성의 이름을 맞춰주면 -->
<input type="checkbox" id="subscribe">
<!-- input 대신 label을 눌러도 input 선택 가능 -->
<label for="subscribe">누르기</label>
```

### 동시에 여러 요소에 한 스타일을 주기

```css
/* 셀렉터에 콤마(,)를 사용하기 */
div, input, textarea {
  box-sizing: border-box;
}
```

### vertical-align 사용하기

- 테이블 셀 내에서 상하 정렬 하기 (top, bottom, middle 사용 가능)

  ```css
  td, th {
    vertical-align : middle;
  }
  ```

- inline 요소간 상하 정렬하기 (top, middle, bottom, super, sub, px 단위 사용 가능)
  
  ```html
  <p>
  <span style="font-size : 50px">Hello</span>
  <span style="font-size : 20px; vertical-align: top">World</span>
  </p>
  ```

### nth-child 셀렉터

- 테이블에서 원하는 순서의 셀에 스타일줄 때 유용하게 사용
- 숫자 외 even, odd, 3n+0로도 가능

  ```css
  /* .cart-table 안의 td 중, 2번째 td에만 color 주기 */
  .cart-table td:nth-child(2) {
    color: red;
  } 
  ```

### border-top/bottom

- 테두리 색상 위, 아래에만 넣고 싶을 때 사용

  ```css
  td, th {
    border-bottom : 1px solid black;
  }
  ```

### 셀 블록마다 width 손쉽게 설정하기

- 하나의 td에 width를 주어도 전체 열의 width가 변해서 매우 편리함

  ```html
  <table>
  <tr>
    <td class="name">상품명</td>
    <td class="price">가격</td>
    <td>수량</td>
    </tr>
  </table>
  ```

  ```css
  .name {
    width : 50%
  }
  .price {
    width : 20%
  }
  ```

### td 여러개를 합치고 싶다면: colspan

- colspan에 원하는 숫자를 넣으면 그 숫자만큼 옆의 셀을 합쳐줌

  ```html
  <td colspan="4"></td>
  ```

### 상태에 따라서 스타일을 줄 수 있는 Pseudo-class 셀렉터

- button: 넣을 때는 넣는 순서가 중요함 (hover > focus > active)

  ```css
  .btn:hover {
    background : chocolate; /* 마우스를 올려놓을 때 */
  }
  .btn:focus {
    background : red; /* 클릭 후 계속 포커스 상태일 때 */
  }
  .btn:active {
    background : brown; /* 클릭 중일 때 */
  }
  ```

- input

  ```css
  .input:focus {
    border : 2px solid red;
  }
  ```

- a 태그

  ```css
  /* 방문 전 링크 */ 
  a:link { 
  color : red;
  }

  /* 방문 후 링크 */ 
  a:visited { 
    color : black;
  }
  ```

### 코드양이 줄어드는 [OOCSS] : 뼈대와 살을 분리하자

- 버튼의 기본 스타일인 padding, font-size 이런걸 정의하는 class를 하나 만들고
- 버튼에 스킨 색깔놀이 하는 용도의 class를 여러 개 만들어두는 것

  ```html
  <button class="main-btn bg-red">빨간버튼</button>
  <button class="main-btn bg-blue">파란버튼</button>
  ```

  ```css
  .main-btn {
    font-size : 20px;
    padding : 15px;
    border : none;
    cursor : pointer;
  }

  /* utility class 만들어 두기 */
  .bg-red {
    background : red;
  }
  .bg-blue {
    background : blue;
  }

  .font-small {
    font-size : 12px;
  }
  .font-medium {
    font-size : 16px;
  }
  .font-lg {
    font-size : 20px;
  }
  ```

### font-family

- 사용자의 컴퓨터에 설치되지 않은 폰트를 사이트에서 이용하려면

  ```css
  @font-face {
    font-family : '나눔고딕 폰트';
    src : url(nanumsquare.ttf)
  }
  ```

- Windows 환경에서 글자가 깨진다면 꿀팁: Anti-aliasing

  ```css
  transform : rotate(0.04deg); 
  ```

### 유용한 Emmet 단축키

> Reference: [하늘네트](https://www.hanl.tech/blog/emmet-%EB%8B%A8%EC%B6%95%ED%82%A4-%EB%B0%8F-%ED%8A%B8%EB%A6%AD-9%EA%B0%80%EC%A7%80/)

- HTML5 boilerplate (표준문서): 2가지 방법
  - “!”치고 “tab”; 또는 “HTML”입력 후 “HTML:5” 선택
- 하위 요소 생성: “>” 사용
  - header>ul>li
- 동급 요소 생성: “+” 사용
  - section>article>h2+p
- 반복 태그 생성: “*” 사용
  - ul>li*5
- CSS class 와 id 설정: “.” 와 “#”사용
  - ul#menu>li.item*3
- 텍스트가 있는 태그: {} 중괄호 안에 {텍스트}를 입력
  - a.button{Click Me}

### Favicon(파비콘) 넣기

- 32 x 32 사이즈, ico로 넣기
  
  ```html
  <head>
  <link rel="icon" href="아이콘경로.ico" type="image/x-icon">
  </head>
  ```

### 여러가지 meta 태그

```html
<head>
  <!-- 사이트의 인코딩 형식 지정 -->
  <meta charset="UTF-8">

  <!-- 사이트의 검색 결과 화면에 뜨는 문구 수정 -->
  <meta name="description" content="html 잘하는 코딩애플입니다.">
  <meta name="keywords" content="HTML,CSS,JavaScript,자바스크립트,코딩">

  <!-- name="viewport": 사이트 초기 zoom 레벨이나 폭을 지정 -->
  <!-- width=device-width: 모바일 기기의 실제 가로폭을 보고 렌더링하라 -->
  <!-- initial-scale=1 이 부분은 접속시의 화면 줌레벨 설정 -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

### Open Graph

- 페이스북, 카카오톡 등에 링크 공유 시 뜨는 문구 커스터마이징

  ```html
  <head>
    <meta property="og:image" content="/이미지경로.jpg">
    <meta property="og:description" content="사이트설명">
    <meta property="og:title" content="사이트제목">
  </head>
  ```

### 모던 웹에서 사용하는 단위정리

```css
.box {
  width : 16px; /* 기본 px 단위 */
  width : 1.5rem; /* html태그 혹은 기본 폰트사이즈의 1.5배 */
  width : 2em; /* 내 폰트사이즈 혹은 상위요소 폰트사이즈의 2배 */
  width : 50vw; /* 브라우저(viewport) 화면 폭의 50% */
  width : 50vh; /* 브라우저(viewport) 화면 높이의 50% */
}
```

### media query 사용 방법

- CSS 파일 최하단에 사용하며, class를 밑에 하나 더 추가해주는 셈이다. 추가 시 class 안의 font-size 스타일 중복이 발생하는데, 중복 발생 시 더 밑에 있는 스타일을 적용해 준다.

  ```css
  /* 현재 브라우저의 폭이 1200px 이하일 경우, 안에 있는 class를 적용 */
  @media screen and (max-width: 1200px) {
    .box {
      font-size: 400px;
    }
  }
  
  /* 현재 브라우저의 폭이 768px 이하일 경우, 안에 있는 class를 적용 */
  @media screen and (max-width: 768px) {
    .box {
      font-size: 30px;
    }
  }
  ```

### 권장 Breakpoint

- breakpoint: media query 문법 max-width 안에 넣는 브라우저 폭
- 권장 사이즈
  - 1200px, 992px, 768px, 576px
  - 이 중 태블릿: 1200px, 모바일: 768px 두 개를 가장 많이 사용

### Animation 구현하기 4단계

- overlay-wrap에 hover 시, 안에 있는 overlay-black 박스를 위로 올리는 코드 예시

  ```html
    <div class="overlay-wrap">
    <div class="overlay-black">
      <span>hello world</span>
    </div>
    </div>
    <img src="img/product1.jpg">
  ```

1. 시작 스타일 정하기

    ```css
    .overlay-wrap {
    position : absolute;
    width : 100%;
    height : 100%;
    overflow : hidden
    }
    ```

2. 최종 스타일 정하기

    ```css
   .overlay-black {
     width : 100%;
     height : 100%;
     background : rgba(0,0,0,0.3);
     padding : 20px;
     margin-top : 100%;
   }
    ```

3. 언제 최종스타일로 변할지 트리거 주기 (대부분 hover)

    ```css
    .overlay-wrap:hover .overlay-black {
      margin-top : 50%;
    }
    ```

4. transition 으로 동작하게 만들기

    ```css
    .overlay-black {
      width : 100%;
      height : 100%;
      background : rgba(0,0,0,0.3);
      padding : 20px;
      margin-top : 100%;
      transition: all 1s;
    }
    ```

### CSS 덮어쓰기 잘 하는 방법

1. 같은 클래스명이나 스타일을 하단에 작성하기
   - 같은 class 명이라도 하단에 정의한 클래스 명과 스타일을 우선적으로 적용된다.
   - CSS파일이 여러개 첨부되어있을 때도 유효하다. (e.g. 상단에 적용한 main.css < 하단에 적용한 main2.css)
2. id, style 등 우선순위를 높여 작성하기
   - tag < class << id <<< style="" <<<< !important 순으로 우선순위가 높다.
   - 하지만 추후 추가 수정 시를 대비해 근본적인 해결 방안은 아님
3. Specificity (구체성) 높여서 작성하기
   - `div.container .box` 대신, `div.container div.box` 이런 식으로 셀렉터를 여러 개 구체적으로 나열하면 후자가 (더 상단에 있더라도) 덮어써서 적용됨
   - 따라서 추후 덮어쓰는 상황을 염두해서 class 이름은 하나만 써서 작성하는 것이 좋음

### pseudo-class와 pseudo-element

- pseudo-class: 특정 요소가 **다른 상태일 때** 스타일을 줄 수 있게 해줌 `:`
- pseudo-element: **내부의 일부분만** 스타일을 줄 수 있게 해줌 `::`

  ```css
  /* 첫 번째 글자만 스타일링 */
  .text::first-letter {
    color : red;
  }

  /* 첫 번째 줄만 스타일링 */
  .text::first-line {
    color : red;
  }

  /* 마지막 요소만 스타일링 */
  .text::after {
    content : '내용';
    color : red;
  }

  /* 첫 번째 요소만 스타일링 */
  .text::before {
    content: '🔗';
    color : red;
  }
  ```

### Shadow DOM

- HTML 개발시 코드가 너무 복잡해지지 않기 위해 **숨겨놓은 HTML 요소들**
- 크롬 개발자 도구 설정에서 아래와 같이 체크해서 숨겨진 요소들까지 볼 수 있음

  ![Shadow DOM](/Image/shadow_dom_1.png)
- 혹은 개발자도구 우측 하단에서도 selector 확인 후 가져오면 됨

  ![Shadow DOM](/Image/shadow_dom_2.png)
- Shadow DOM 사용 시, input과 같은 기본 모듈까지 커스터마이징 가능

  ```css
  input::-webkit-input-placeholder {
  color : red; 
  }
  ```

### 비디오 넣기

```html
<video autoplay muted loop poster="썸네일경로" preload="metadata">
  <source src="파일경로">
</video>
```

- muted: 음소거상태
- autoplay: 자동재생 (muted와 함께 넣어야 동작)
- poster: 썸네일이미지
- loop: 무한 재생
- preload: 영상 먼저 다운로드 여부 (auto, metadata, none 사용 가능)
- source 파일 형식이 여러 개 있을 경우, 브라우저에 최적화된 비디오 파일을 알아서 넣어 주므로 여러가지 확장자의 비디오 파일이 있으면 `<source>` 여러 개 넣는 것도 좋은 방법임

### 비디오를 배경으로 넣기

```html
<div class="video-box">
  <video class="video-container" autoplay muted loop>
    <source src="img/brand-film.mp4" type="video/mp4">
  </video>
  <h3 class="video-title">Introduce our Brand</h3>
</div>
```

```css
.video-box {
  height: 500px;
  width: 100%;
  overflow: hidden;
  position: relative;
}

.video-container {
  position: absolute;
  width : 100%;
  top: 50%;
  left: 50%;
  transform : translate(-50%,-50%);
  z-index: -1;
}
```

### 텍스트 가운데 정렬하기 (가로, 세로)

> Reference: [hi.anna](https://hianna.tistory.com/674)

#### 가로로 가운데 정렬하기

- text-align 사용

  ```css
  .my-div {
    border: 1px solid blue;
    height: 200px;
    text-align: center;
  }
  ```

- justify-content 사용

  ```css
  .my-div {
    border: 1px solid blue;
    height: 200px;
    display: flex;
    justify-content: center;
  }
  ```

#### 세로로 가운데 정렬하기

- padding 사용

  ```css
  .my-div {
    border: 1px solid blue;
    text-align: center;
    padding: 100px 0;
  }
  ```

- line-height 사용 (div의 height 값과 같게)

  ```css
  .my-div {
    border: 1px solid blue;
    height: 200px;
    text-align: center;
    line-height: 200px;
  }
  ```

- align-items 사용

  ```css
  .my-div {
    border: 1px solid blue;
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  ```

### @keyframes로 transition 주기

`transition`의 속도에는 최소 시간 간격이 존재하며, 이는 브라우저의 렌더링과 animation 처리 속도에 따라 달라질 수 있다. 대부분의 브라우저에서 0.1초보다 더 짧은 시간은 잘 적용되지 않을 수 있다. 브라우저가 animation을 처리하는 속도에 따라 다양한 영향을 받기 때문.

0.1초 이하의 값을 사용하려면, `transition`보다 더 짧은 시간 간격을 가지는 `requestAnimationFrame`을 사용하여 animation을 구현하는 것이 더 나은 접근 방식일 수 있다. 이렇게 하면 브라우저의 렌더링 주기에 더 가깝게 animation을 동작시킬 수 있다.

```css
.carousel-item {
    transition: transform 0.2s;
}

.carousel-item:hover {
    animation: scaleUp 0.05s forwards;
}

@keyframes scaleUp {
    from {
        transform: scale(1);
    }
    to {
        transform: scale(1.05);
    }
}
```

위 코드에서는 `animation` 속성을 사용하여 `scaleUp`라는 animation을 정의하고, 이 animation을 `hover` 상태일 때 동작하도록 설정했다. `@keyframes`를 사용하여 animation의 시작과 끝을 정의하며, 이렇게 하면 좀 더 짧은 시간 간격으로 빠르게 animation을 적용할 수 있다.

### transform 관련 CSS 속성들

```css
.box {
  transform : rotate(10deg); /* 회전 */
  transform : translate(10px, 20px); /* 좌표 이동 */
  transform : scale(2); /* 확대 or 축소 */
  transform : skew(30deg); /* 비틀기 */
  
  /* transform 두개 이상 사용 */
  transform : rotate(10deg) translateX(30px);
}
```

### keyframes 사용하기

```css
@keyframes move-move {
  0% {
    transform : translateX(0px); /* animation이 0%만큼 동작시 */
  }
  50% {
    transform : translateX(-20px); /* animation이 50%만큼 동작시 */
  }
  100% {
    transform : translateX(20px); /* animation이 100%만큼 동작시 */
  }
}
```

```css
/* animation 적용 시 꼭 필요한 항목 */
.box:hover {
  animation-name : move-move; /* 위에서 작성한 이름 붙여줌 */
  animation-duration : 1s;
}
```

```css
/* animation 세부 조정하기 */
.box:hover {
  animation-name : move-move;
  animation-duration : 1s;
  animation-timing-function : linear; /* 베지어 주기 */
  animation-delay : 1s; /* 시작 전 딜레이 */
  animation-iteration-count : 3; /* 반복 횟수 */
  animation-play-state : paused;  /* animation을 멈추고 싶은 경우 자바스크립트로 조정 */
  animation-fill-mode: forwards;  /* animation 끝난 후에 원상복구 하지 않고 정지 */
}
```

### margin, width, left이 아닌 transform을 사용하는 이유

- 웹 브라우저들은 HTML/CSS를 2D 그래픽으로 바꿔주는데, HTML/CSS을 그래픽으로 바꿀 때 [layout 잡기 → 색칠하기 → transform 적용하기] 순서로 동작함
- layout이 바뀌면 layout(e.g. margin, width 등) 부터 transform 까지 쭉 다시 렌더링 해야하는데, transform이 바뀌면 transform 부분만 다시 렌더링하면 되기 때문.
- 따라서 animation 적용 시 margin보다 transform를 사용하면 빠르게 동작함

### 성능 개선하기

- will-change : 바뀔 내용을 미리 렌더링해주는 속성임

  ```css
  .box {
    /* will-change : 애니메이션 줄 속성 */
    will-change: transform;
  }
  ```

- 하드웨어 가속: GPU의 도움을 받아 연산하기에 translate()보다 성능이 더 좋음

  ```css
  /* 아무데도 움직이지 않는 3D 이동명령을 주고, 뒤에 필요한 transform을 더 적용한다면 
  GPU를 이용해 .box가 가진 transform 속성들을 연산할 수 있음 */
  .box {
    transform: translate3d(0, 0, 0);
  }
  ```

### Grid 사용법

```css
.grid-container {
  display: grid;

  /* 격자 열 너비와 갯수, fr는 몇 배만큼 차지할지 값 */
  grid-template-columns: 1fr 1fr 1fr 1fr;

  /* 격자 행 높이와 갯수 */
  grid-template-rows: 100px 100px 100px;

  grid-gap: 10px;
}
```

### Grid로 레이아웃 만드는 법 (1) 자식 div 높이와 폭을 조정하기

```html
<div class="grid-container">
    <div class="grid-nav">헤더</div>
    <div class="grid-sidebar">사이드바</div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
</div>
```

```css
.grid-nav {
  grid-column : 1 / 4; /* 세로선 1부터 4까지 차지 */
  grid-row : 2 / 4;
}
```

### Grid로 레이아웃 만드는 법 (2) 자식에게 이름쓰고 부모가 배치하기

```css
.grid-nav {
  grid-area: 헤더;
}

.grid-sidebar {
  grid-area: 사이드바;
}
```

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 100px 100px 100px;
  grid-gap: 10px;
  grid-template-areas: 
    "헤더 헤더 헤더 헤더"
    "사이드 사이드 . ."
    "사이드 사이드 . ."
}
```

```css
/* 반응형은 이렇게 */
@media screen and (max-width : 768px){
  .grid-container2 {
    grid-template-areas: 
    "헤더 헤더 헤더 헤더"
    "사이드바 사이드바 사이드바 사이드바"
    "내용 내용 내용 내용";
  }
}
```

### position: sticky 사용하기

`position : fixed` 는 항상 화면에 고정이 되는 요소를 만들 때 사용하지만, `position : sticky` 는 스크롤이 되어서 이 요소가 화면에 나오면 고정시킴. 이때, (1) 스크롤을 할 만한 부모 박스가 있어야 하고, (2) top 등 좌표속성과 함께 써야 제대로 보임

  ```css
  /* 
  1. 스크롤이 되어서 이미지가 보이는 순간
  2. viewport의 맨 위에서부터 100px 위치에서 고정됨
  3. 그리고 부모 박스를 넘어서 스크롤 되면 이미지도 같이 사라짐
  */

  .grey {
    background: lightgrey;
    height: 2000px;
    margin-top: 500px;
  }
  .text {
    float: left;
    width : 300px;
  }
  .image {
    float: right;
    width : 400px;
    position: sticky;
    top: 100px;
  }
  ```

### CSS 3D animation

```css
transform : rotateX(180deg);
transform : rotateY(180deg);
transform : rotateZ(180deg);
```

