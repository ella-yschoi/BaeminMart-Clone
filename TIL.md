# Today I Learned

## What I learned about HTML?

### 1. 이미지 가운데 정렬하는 방법

```html
display: block;
margin-left: auto;
margin-right: auto
```

### 2. 문장 안의 일부 글자만 스타일링 하는 방법

- span 태그는 `display : inline` 이라는 스타일 속성을 내포하고 있기에
- `display : inline`을 가지고 있는 요소는 폭, 높이 등을 단독으로 결정할 수 없음
- 폭, 높이를 주고싶으면 이를 감싸고 있는 `<p>`에 주기

```html
<p>이건<span style="color: yellow;">일부</span>문장</p>
```

### 3. selector 용어 정리

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
```

### 4. display: block이 내장되어 있는 div

- 모든 `<div>`, `<p>`, `<h1>`, `<li>` 등은 `display : block` 속성을 주지 않아도 기본적으로 내장되어 있음. 그래서 `<div>`, `<p>`를 그냥 사용하면 한 행을 전부 차지하게 됨.
- 이렇게 하고 싶지 않다면 display 속성을 `inline`, `inline-block`, `flex` 등으로 주면 됨.

### 5. 일부 스타일은 inherit(상속) 됨

- `font-size`, `color`, `font-family`, `text-align` 속성은 부모태그에 적용하면 안에 있던 자식 태그들에까지 모두 상속됨
