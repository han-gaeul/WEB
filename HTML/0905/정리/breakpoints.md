### `Breakpoints (์ค๋จ์ )`

***

##### ๐ก Breakpoints๋?

๋ถํธ์คํธ๋ฉ์์ ์ฅ์น ๋๋ ๋ทฐํฌํธ ํฌ๊ธฐ์ ๊ฑธ์ณ ๋ฐ์ํ ๋ ์ด์์์ด ์๋ํ๋ ๋ฐฉ์์ ๊ฒฐ์ ํ๋ ์ฌ์ฉ์ ์ง์  ๊ฐ๋ฅํ ๋๋น





##### ๐ก ํต์ฌ ๊ฐ๋

- `breakpoints`๋ ๋ฐ์ํ ์ค๊ณ์ ๊ธฐ๋ณธ ์์
  - ๋ ์ด์์์ ํน์  ๋ทฐํฌํธ ๋๋ ์ฅ์น ํฌ๊ธฐ์ ๋ง๊ฒ ์กฐ์ ํ  ์ ์๋ ์๊ธฐ๋ฅผ ์ ์ดํ๋๋ฐ ์ฌ์ฉ
- ๋ฏธ๋์ด ์ฟผ๋ฆฌ๋ฅผ ์ฌ์ฉํ์ฌ `breakpoints`๋ณ๋ก CSS๋ฅผ ์ค๊ณ
  - ๋ฏธ๋์ด ์ฟผ๋ฆฌ๋ ๋ธ๋ผ์ฐ์  ๋ฐ ์ด์ ์ฒด์  ๋งค๊ฐ ๋ณ์ ์งํฉ์ ๊ธฐ๋ฐํ์ฌ ์คํ์ผ์ ์กฐ๊ฑด๋ถ๋ก ์ ์ฉํ  ์ ์๋ CSS์ ๊ธฐ๋ฅ.
  - ๋ฏธ๋์ด ์ฟผ๋ฆฌ์์ ๊ฐ์ฅ ์ผ๋ฐ์ ์ผ๋ก ์ต์ ๋๋น๋ฅผ ์ฌ์ฉ
- ๋ชจ๋ฐ์ผ ์ฐ์ , ๋ฐ์ํ ๋์์ธ์ด ๋ชฉํ
  - ๋ถํธ์คํธ๋ฉ์ CSS๋ ์ต์ํ์ ์คํ์ผ์ ์ ์ฉํ์ฌ ๊ฐ์ฅ ์์ `breakpoints`์์ ๋ ์ด์์ ์์์ ํ ๋ค์ ์คํ์ผ์ ๋ ์ด์ดํ์ฌ ๋ ํฐ ์ฅ์น์ ๋ง๊ฒ ๋์์ธ์ ์กฐ์ ํ๋ ๊ฒ์ ๋ชฉํ๋ก ํจ
  - CSS๋ฅผ ์ต์ ํํ๊ณ  ๋ ๋๋ง ์๊ฐ์ ๊ฐ์ 





##### โ๏ธ ์ฌ์ฉ ๊ฐ๋ฅํ Breakpoints

| Breakpoint        | Class infix | Dimensions |
| ----------------- | ----------- | ---------- |
| Extra small       | *None*      | <576px     |
| Small             | sm          | โฅ576px     |
| Medium            | md          | โฅ768px     |
| Large             | lg          | โฅ992px     |
| Extra large       | xl          | โฅ1200px    |
| Extra extra large | xxl         | โฅ1400px    |

- Sass๋ฅผ ํตํด ์ฌ์ฉ์ ์ ์ ํ  ์ ์์

```css
$grid-breakpoints: (
xs: 0,
sm: 576px,
md: 768px,
lg: 992px,
xl: 1200px,
xxl: 1400px
);
```





##### โ๏ธ Media queries (๋ฏธ๋์ด ์ฟผ๋ฆฌ)

- ๋ถํธ์คํธ๋ฉ์ ๋ชจ๋ฐ์ผ ์ฐ์ ์ผ๋ก ๊ฐ๋ฐ ๋์์ผ๋ฏ๋ก ๋ช ๊ฐ์ง ๋ฏธ๋์ด ์ฟผ๋ฆฌ๋ฅผ ์ด์ฉํด ๋ ์ด์์์ ์ ํฉํ `breakpoints`๋ฅผ ๋ง๋ ๋ค
  - ์ด๋ฌํ `breakpoints`๋ ๋๋ถ๋ถ ์ต์ ๋ทฐํฌํธ ๋์ด๋ฅผ ๊ธฐ๋ฐ์ผ๋ก ํ๋ฉฐ ๋ทฐํฌํธ๋ฅผ ๋ณ๊ฒฝํจ์ ๋ฐ๋ผ ์์๋ฅผ ํ์ฅ ํ  ์ ์์

- `Min-width`

  ```css
  /* Source mixins */
  /* 'xs' breakpoints๋ `@media (min-width: 0) { ... }` ์ด๋ฏ๋ก ๋ฏธ๋์ด ์ฟผ๋ฆฌ๊ฐ ํ์ํ์ง ์์*/
  @include media-breakpoint-up(sm) { ... }
  @include media-breakpoint-up(md) { ... }
  @include media-breakpoint-up(lg) { ... }
  @include media-breakpoint-up(xl) { ... }
  @include media-breakpoint-up(xxl) { ... }
  
  
  /* ์ฌ์ฉ */
  /* ์) 'min-width: 0'์ผ๋ก ์์ํ๋ ๊ฒ์ ์จ๊ธด ๋ค์ 'sm' breakpoints์ ํ์ */
  .custom-class {
    display: none;
  }
  @include media-breakpoint-up(sm) {
    .custom-class {
      display: block;
    }
  }
  ```

  ```css
  /* X-Small ๊ธฐ๊ธฐ (์ธ๋ก ๋ฐฉํฅ์ ํธ๋ํฐ, 576px ๋ฏธ๋ง) */
  /* ๋ถํธ์คํธ๋ฉ์ ๊ธฐ๋ณธ๊ฐ์ด๊ธฐ ๋๋ฌธ์ 'xs'์ ๋ํ ๋ฏธ๋์ด ์ฟผ๋ฆฌ๊ฐ ์์ */
  
  /* Small ๊ธฐ๊ธฐ (๊ฐ๋ก ๋ฐฉํฅ์ ํธ๋ํฐ, 576px ์ด์) */
  @media (min-width: 576px) { ... }
  
  /* Medium ๊ธฐ๊ธฐ (ํ๋ธ๋ฆฟ, 768px ์ด์) */
  @media (min-width: 768px) { ... }
  
  /* Large ๊ธฐ๊ธฐ (๋ฐ์คํฌํฑ, 992px ์ด์) */
  @media (min-width: 992px) { ... }
  
  /* X-Large ๊ธฐ๊ธฐ (๋ํ ๋ฐ์คํฌํฑ, 1200px ์ด์) */
  @media (min-width: 1200px) { ... }
  
  /* XX-Large ๊ธฐ๊ธฐ (๋ํ ๋ฐ์คํฌํฑ, 1400px ์ด์) */
  @media (min-width: 1400px) { ... }
  ```

- `Max-width`

  ```css
  /* 'xs' breakpoints๋ `@media (min-width: 0) { ... }` ์ด๋ฏ๋ก ๋ฏธ๋์ด ์ฟผ๋ฆฌ๊ฐ ํ์ํ์ง ์์*/
  @include media-breakpoint-down(sm) { ... }
  @include media-breakpoint-down(md) { ... }
  @include media-breakpoint-down(lg) { ... }
  @include media-breakpoint-down(xl) { ... }
  @include media-breakpoint-down(xxl) { ... }
  
  /* ์) */
  @include media-breakpoint-down(md) {
    .custom-class {
      display: block;
    }
  }
  ```

  ```css
  /* X-Small ๊ธฐ๊ธฐ (์ธ๋ก ๋ฑกํฅ์ ํธ๋ํฐ, 576px ๋ฏธ๋ง) */
  @media (max-width: 575.98px) { ... }
  
  /* Small ๊ธฐ๊ธฐ (๊ฐ๋ก ๋ฐฉํฅ์ ํธ๋ํฐ, 768px ๋ฏธ๋ง) */
  @media (max-width: 767.98px) { ... }
  
  /* Medium ๊ธฐ๊ธฐ (ํ๋ธ๋ฆฟ, 992px ๋ฏธ๋ง) */
  @media (max-width: 991.98px) { ... }
  
  /* Large ๊ธฐ๊ธฐ (๋ฐ์คํฌํฑ, 1200px ๋ฏธ๋ง) */
  @media (max-width: 1199.98px) { ... }
  
  /* X-Large ๊ธฐ๊ธฐ (๋ํ ๋ฐ์คํฌํฑ, 1400px ๋ฏธ๋ง) */
  @media (max-width: 1399.98px) { ... }
  
  /*  XX-Large devices (larger desktops) */
  /* 'xxl' breakpoint ๋๋น์ ์ํ์ด ์์ผ๋ฏ๋ก ๋ฏธ๋์ด ์ฟผ๋ฆฌ๊ฐ ์์ */
  ```

- `Single breakpoint`

  ```css
  @include media-breakpoint-only(xs) { ... }
  @include media-breakpoint-only(sm) { ... }
  @include media-breakpoint-only(md) { ... }
  @include media-breakpoint-only(lg) { ... }
  @include media-breakpoint-only(xl) { ... }
  @include media-breakpoint-only(xxl) { ... }
  
  /* ์) @include media-breakpoint-only(md) { ... } */
  @media (min-width: 768px) and (max-width: 991.98px) { ... }
  ```

- `Between breakpoints`

  ```css
  @include media-breakpoint-between(md, xl) { ... }
  
  /* ์ */
  /* ์คํ ์ฅ์น๋ถํฐ ์ด๋ํ ์ฅ์น๊น์ง ์คํ์ผ์ ์ ์ฉํ  ์ ์์ */
  @media (min-width: 768px) and (max-width: 1199.98px) { ... }
  ```

  