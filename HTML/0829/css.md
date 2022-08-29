### `CSS : Cascading Style Sheets`

***

- HTML이나 XML로 작성된 문서의 표시 방법을 기술하기 위한 스타일 시트 언어
- 요소가 화면, 종이, 음성이나 다른 매체 상에 어떻게 렌더링 되어야 하는지 지정
- 오픈 웹의 핵심 언어 중 하나





#### 📌CSS 기초

- rule set

  - `선택자(selector)`
    - rule set의 맨 앞에 있는 HTML 요소 이름
    - 꾸밀 요소들을 선택함
    - 다른 요소를 꾸미기 위해서는 선택자만 변경

  - `선언`
    - 'color: red'와 같은 단일 규칙
    - 꾸미기 원하는 요소의 속성을 명시

  - `속성(property)`
    - 주어진 HTML 요소를 꾸밀 수 있는 방법
    - CSS에서, rule 내에서 영향을 줄 속성을 선택

  - `속성 값`

    - 각각의 rule set(셀렉터로 구분)은 반드시 '{}'로 감싸져야 함
    - 각각의 선언 안에 각 속성을 해당 값과 구분하기 위해 콜론(:)을 사용해야 함
    - 각각의 rule set 안에, 각 선언을 그 다음 선언으로부터 구분하기 위해 세미콜론(;)을 사용해야 함

    ```css
    p {
      color: red;
      width: 500px;
      border: 1px solid black;
    }
    ```

- 여러 요소 선택하기

  - 요소의 여러 타입을 선택하고 모두에게 하나의 rule set을 적용
  - 여러 선택자는 콤마(,)로 구분

  ```css
  p,li,h1 {
    color: red;
  }
  ```

- 선택자의 여러 종류

  | 선택자 이름                                          | 선택하는 것                                                  | 예시                                                         |
  | ---------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | 요소 선택자<br>(때때로 태그 또는 타입 선택자라 불림) | 특정 타입의 모든 HTML 요소                                   | `p`<br>`<p>를 선택`                                          |
  | 아이디 선택자                                        | 특정 아이디를 가진 페이지의 요소<br>(주어진 HTML 페이지에서 아이디당 딱 하나의 요소만 허용 됨) | `#my-id`<br>`<p id="my-id">`<br>또는 `<a id="my-id">`를 선택 |
  | 클래스 선택자                                        | 특정 클래스를 가진 페이지의 요소<br>(한 페이지에 클래스가 여러번 나타날 수 있음) | `.my-class`<br>`<p calss="my-class">`와<br>`<a class="my-class">`를 선택 |
  | 속성 선택자                                          | 특정 속성을 갖는 페이지의 요소                               | `img[src]`<br>`<img src="myimage.png">`를 선택하지만<br>`<img>`는 선택 안 함 |
  | 수도(Pseudo) 클래스 선택자                           | 특정 요소이지만 특정 상태에 있을 때만,<br>예) hover over 상태일 때 | `a:hover` `<a>`를 선택하지만,<br>마우스 포인터가 링크 위에 있을 때만 선택함 |

- 글꼴과 문자

  - [Google Fonts](https://fonts.google.com/) 에서 폰트를 선택해서 `html ` 파일의 `<head>` 안에 `<link>` 요소를 추가

  ```css
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100&display=swap" rel="stylesheet">
  ```

  - `css` 파일에 이미 존재하는 rule을 지움

  - 아래의 코드를 해당 위치에 추가하고 구글 폰트로부터 얻은 `font-family` *(글자를 위해 사용하길 원하는 글꼴 의미)* 코드를 placeholder 줄에 덮어씀

    이 rule은 먼저 전체 페이지의 글자 크기와 기본 글꼴을 설정

    *(html이 전체 페이지의 부모 요소일 때, 이 안의 모든 요소는 같은 font-size와 font-famliy를 물려 받음*

    ```css
    html {
      font-size: 10px; /* px 은 'pixels' 를 의미: 기본 글자 크기는 현재 10 pixels 높이 */
      font-family: placeholder: 구글 폰트로부터 얻은 마지막 결과가 있어야함
    }
    ```

- 박스

  - `padding` : 컨텐츠 주위의 공간 *(예 : 문단 글자의 주위)*
  - `border` : padding의 바깥쪽에 놓인 실선
  - `margin` : 요소의 바깥쪽을 둘러싼 공간
  - `width` : 한 요소의 너비
  - `background-color` : 요소의 콘텐츠와 padding의 배경 색
  - `color` : 한 요소의 콘텐츠 색 *(일반적으로 글자색)*
  - `text-shadow` : 한 요소 안의 글자에 그림자를 적용
  - `display` : 요소의 표시 형식을 설정

- 페이지 색 바꾸기

  - 전체 페이지를 위한 배경색을 설정

  ```css
  html {
    background-color: #00539F;
  }
  ```

- body 외부 정렬하기

  ```css
  body {
    width: 600px;
    margin: 0 auto;
    background-color: #FF9500;
    padding: 0 20px 20px 20px;
    border: 5px solid black;
  }
  ```

  - `width: 600px;` : body가 항상 600 pixels의 너비를 갖도록 강제

  - `margin: 0 auto;` : margin 또는 padding처럼 한 속성에 두 개의 값을 설정할 때

    첫 번째 값은 요소의 상단과 하단에 영향을 주고, 두 번째 값은 좌측과 우측에 영향을 줌

    *(auto는 가능한 수평공간의 왼쪽과 오른쪽을 같게 나눠주는 특별한 값)*

  - `background-color: #FF9500;` : 요소의 배경색을 설정

  - `padding: 0 20px 20px 20px;` : 콘텐츠 주위에 약간의 공간을 주기 위해 네 개의 값을 설정

    상단, 우측, 하단, 좌측 순서로 값을 설정 *(12시부터 시계 방향)*

  - `border: 5px solid black;`: 간단하게 body 모든 면의 border를 5 pixels 두께의 실선으로 설정

- 이미지 가운데 정렬

  ```css
  img {
    display: block;
    margin: 0 auto;
  }
  ```

  