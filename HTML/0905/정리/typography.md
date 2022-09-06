### `Typography`

***

##### 💡 Global settings

- 부트스트랩은 기본적인 글로벌 디스플레이, 타이포그래피 및 링크 스타일을 설정

  - 각 OS 및 장치에 대한 `font-family` 이다
  - 보다 포괄적이고 접근하기 쉬운 유형 확장을 위해 브라우저의 기본 루트 `font-size`(일반적으로 16px)를 사용하여 방문자가 필요에 따라 브라우저 기본값을 사용자 지정할 수 있음
  - `$font-family-base`, `$font-size-base`, `$line-height-base` 속성을 `<body>`에 적용되는 타이포그래피 기준으로 사용
  - `$link-color`를 통해 글로벌 링크 색상을 설정
  - `$body-bg`를 사용하여 `<body>`에 배경색을 설정 *(기본값 #ffff)*

- 이런 스타일은 `_reboot.scss` 내에서 찾을 수 이으며 전역 변수는 `_variables.scss`에서 정의

  `$font-size-base`를 `rem`으로 설정해야 함

  