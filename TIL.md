# Today I Learned

## What I learned about HTML & CSS?

### 1. 이미지 가운데 정렬하는 방법

```html
display: block;
margin-left: auto;
margin-right: auto
```

### 2. 문장 안의 일부 글자만 스타일링 하는 방법

```html
<p>이건<span style="color: yellow;">일부</span>문장</p>
```

- span 태그는 `display : inline` 이라는 스타일 속성을 내포하고 있기에
- `display : inline`을 가지고 있는 요소는 폭, 높이 등을 단독으로 결정할 수 없음
- 폭, 높이를 주고싶으면 이를 감싸고 있는 `<p>`에 주기

### 3. selector 사용법

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

### 4. display: block이 내장되어 있는 div

- 모든 `<div>`, `<p>`, `<h1>`, `<li>` 등은 `display : block` 속성을 주지 않아도 기본적으로 내장되어 있음. 그래서 `<div>`, `<p>`를 그냥 사용하면 한 행을 전부 차지하게 됨.
- 이렇게 하고 싶지 않다면 display 속성을 `inline`, `inline-block`, `flex` 등으로 주면 됨.

### 5. 일부 스타일은 inherit(상속) 됨

- `font-size`, `color`, `font-family`, `text-align` 속성은 부모태그에 적용하면 안에 있던 자식 태그들에까지 모두 상속됨

### 6. 요소를 공중에 띄워 왼쪽/오른쪽 정렬하는 float 속성

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

### 7. 텍스트 수평 & 수직 가운데 정렬

```css
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
```

### 8. class 2개 이상 부여하려면

  ```css
  /* class명을 띄어쓰기 후 연달아 작성 */
  <ul class="navbar content">
  ```

### 9. a 태그 링크 설정

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

### 10. position

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

### 11. 박스의 폭을 border까지 설정해주고 싶을 때

```css
.box {
  box-sizing : border-box; /* 박스의 폭은 border까지 포함 */
  box-sizing : content-box; /* 박스의 폭은 padding 안쪽 */
}

.div {
  box-sizing : border-box; /* 보통 css파일 맨 위에 써놓고 시작하면 좋음 */
}
```

### 12. CSS 파일 작성시 기본으로 쓰면 좋을 속성들

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
  a:link { 
  color : red; /* 방문 전 링크 */ 
  }
  a:visited { 
    color : black; /* 방문 후 링크 */ 
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
