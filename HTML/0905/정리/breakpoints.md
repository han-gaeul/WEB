### `Breakpoints (중단점)`

***

##### 💡 Breakpoints란?

부트스트랩에서 장치 또는 뷰포트 크기에 걸쳐 반응형 레이아웃이 작동하는 방식을 결정하는 사용자 지정 가능한 너비





##### 💡 핵심 개념

- `breakpoints`는 반응형 설계의 기본 요소
  - 레이아웃을 특정 뷰포트 또는 장치 크기에 맞게 조정할 수 있는 시기를 제어하는데 사용
- 미디어 쿼리를 사용하여 `breakpoints`별로 CSS를 설계
  - 미디어 쿼리는 브라우저 및 운영 체제 매개 변수 집합에 기반하여 스타일을 조건부로 적용할 수 있는 CSS의 기능.
  - 미디어 쿼리에서 가장 일반적으로 최소 너비를 사용
- 모바일 우선, 반응형 디자인이 목표
  - 부트스트랩의 CSS는 최소한의 스타일을 적용하여 가장 작은 `breakpoints`에서 레이아웃 작업을 한 다음 스타일을 레이어하여 더 큰 장치에 맞게 디자인을 조정하는 것을 목표로 함
  - CSS를 최적화하고 렌더링 시간을 개선





##### ✍️ 사용 가능한 Breakpoints

| Breakpoint        | Class infix | Dimensions |
| ----------------- | ----------- | ---------- |
| Extra small       | *None*      | <576px     |
| Small             | sm          | ≥576px     |
| Medium            | md          | ≥768px     |
| Large             | lg          | ≥992px     |
| Extra large       | xl          | ≥1200px    |
| Extra extra large | xxl         | ≥1400px    |

- Sass를 통해 사용자 정의 할 수 있음

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





##### ✍️ Media queries (미디어 쿼리)

- 부트스트랩은 모바일 우선으로 개발 되었으므로 몇 가지 미디어 쿼리를 이용해 레이아웃에 적합한 `breakpoints`를 만든다
  - 이러한 `breakpoints`는 대부분 최소 뷰포트 넓이를 기반으로 하며 뷰포트를 변경함에 따라 요소를 확장 할 수 있음

- `Min-width`

  ```css
  /* Source mixins */
  /* 'xs' breakpoints는 `@media (min-width: 0) { ... }` 이므로 미디어 쿼리가 필요하지 않음*/
  @include media-breakpoint-up(sm) { ... }
  @include media-breakpoint-up(md) { ... }
  @include media-breakpoint-up(lg) { ... }
  @include media-breakpoint-up(xl) { ... }
  @include media-breakpoint-up(xxl) { ... }
  
  
  /* 사용 */
  /* 예) 'min-width: 0'으로 시작하는 것을 숨긴 다음 'sm' breakpoints에 표시 */
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
  /* X-Small 기기 (세로 방향의 핸드폰, 576px 미만) */
  /* 부트스트랩의 기본값이기 때문에 'xs'에 대한 미디어 쿼리가 없음 */
  
  /* Small 기기 (가로 방향의 핸드폰, 576px 이상) */
  @media (min-width: 576px) { ... }
  
  /* Medium 기기 (태블릿, 768px 이상) */
  @media (min-width: 768px) { ... }
  
  /* Large 기기 (데스크톱, 992px 이상) */
  @media (min-width: 992px) { ... }
  
  /* X-Large 기기 (대형 데스크톱, 1200px 이상) */
  @media (min-width: 1200px) { ... }
  
  /* XX-Large 기기 (대형 데스크톱, 1400px 이상) */
  @media (min-width: 1400px) { ... }
  ```

- `Max-width`

  ```css
  /* 'xs' breakpoints는 `@media (min-width: 0) { ... }` 이므로 미디어 쿼리가 필요하지 않음*/
  @include media-breakpoint-down(sm) { ... }
  @include media-breakpoint-down(md) { ... }
  @include media-breakpoint-down(lg) { ... }
  @include media-breakpoint-down(xl) { ... }
  @include media-breakpoint-down(xxl) { ... }
  
  /* 예) */
  @include media-breakpoint-down(md) {
    .custom-class {
      display: block;
    }
  }
  ```

  ```css
  /* X-Small 기기 (세로 뱡향의 핸드폰, 576px 미만) */
  @media (max-width: 575.98px) { ... }
  
  /* Small 기기 (가로 방향의 핸드폰, 768px 미만) */
  @media (max-width: 767.98px) { ... }
  
  /* Medium 기기 (태블릿, 992px 미만) */
  @media (max-width: 991.98px) { ... }
  
  /* Large 기기 (데스크톱, 1200px 미만) */
  @media (max-width: 1199.98px) { ... }
  
  /* X-Large 기기 (대형 데스크톱, 1400px 미만) */
  @media (max-width: 1399.98px) { ... }
  
  /*  XX-Large devices (larger desktops) */
  /* 'xxl' breakpoint 너비에 상한이 없으므로 미디어 쿼리가 없음 */
  ```

- `Single breakpoint`

  ```css
  @include media-breakpoint-only(xs) { ... }
  @include media-breakpoint-only(sm) { ... }
  @include media-breakpoint-only(md) { ... }
  @include media-breakpoint-only(lg) { ... }
  @include media-breakpoint-only(xl) { ... }
  @include media-breakpoint-only(xxl) { ... }
  
  /* 예) @include media-breakpoint-only(md) { ... } */
  @media (min-width: 768px) and (max-width: 991.98px) { ... }
  ```

- `Between breakpoints`

  ```css
  @include media-breakpoint-between(md, xl) { ... }
  
  /* 예 */
  /* 중형 장치부터 초대형 장치까지 스타일을 적용할 수 있음 */
  @media (min-width: 768px) and (max-width: 1199.98px) { ... }
  ```

  