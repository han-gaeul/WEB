### `CSS 배우기 - Layout`

***

##### ✏️ 디스플레이 속성 이해하기

- 적용되는 박스가 인라인인지, 블록인지 판별

  - 인라인 요소

    - 문장의 단어와 같이 동작. 나란히 배치 됨
    - 명시적인 너비 및 높이를 설정할 수 없음
    - 모든 블록 레벨 여백 및 패딩은 주변 요소에 의해 무시됨

    ```css
    .my-element {
      display: inline;
    }
    ```

  - 블록 요소

    - 서로 나란히 배치되지 않음. 새로운 라인을 만듦
    - 다른 CSS 코드에 의해 변경되지 않는 한 블록 요소는 인라인 치수의 크기로 확장되므로 수평 쓰기 모드에서 전폭에 걸쳐짐
    - 블록 요소의 모든 면에서 여백이 유지됨

    ```css
    .my-element {
      display: block;
    }
    ```







##### ✏️Flexbox and Grid

- Flexbox

  - 1차원 레이아웃을 위한 레이아웃 매커니즘. 수평 또는 수직의 단일 축에 걸쳐 레이아웃함.
  - 기본적으로 요소의 하위 항목을 인라인 방향으로 서로 나란히 정렬하고 블록 방향으로 늘려서 높이가 모두 같도록 함

  ```css
  .my-element {
    display: flex;
  }
  ```

  - 항목이 동일한 축에 유지되고 공간이 부족할 때 접히지 않는 대신 서로 같은 선에 서려고 함

    이 동작은 `align-items`, `justify-content`, `flex-wrap` 속성을 사용해 변경할 수 있음

  - Flexbox는 하위 요소를 플렉스 항목으로 변환함

    - 플렉스 컨테이너 내에서 동작하는 방법에 대한 규칙을 작성할 수 있음
    - 개별 항목의 정렬, 순서 및 정당성을 변경할 수 있음
    - 플렉스 속성을 사용하여 축소 또는 증가 방법을 변경할 수 있음

    ```css
    .my-element dic {
      flex: 1 0 auto;
    }
    ```

    > `felx` 속성은 `flex-grow`, `flex-shrink`, `flex-basis`의 줄임말
    >
    > 위의 예제를 다음과 같이 확장할 수 있음

    ```css
    .my-element dic {
      flex-grow: 1;
      flex-shrink: 0;
      flex-basis: auro;
    }
    ```

- Grid

  - 플렉스 박스와 많이 면에서 유사하지만 단일 축 레이아웃(수직 또는 수평 공간) 대신 다중 축 레이아웃을 제어하도록 설계 됨

  ```css
  .my-element {
    display: grid;
  }
  ```

  - 디스플레이가 있는 요소인 그리드에 레이아웃 규칙을 작성할 수 있음
    - `repeat()` 및 `minmax()` 함수와 같은 레이아웃 스타일링을 위한 몇 가지 새로운 기본 요소를 도입할 수 있음

  ```css
  .my-element {
    display: grid;
    grid-template-columns:repeat(12, 1fr);
    gap: 1rem;
  }
  ```

  - `grid-row`, `grid-column`
    - 예) 그리드의 첫 번째 요소가 첫 번째 열에서 네 번째 열의 시작까지 이어지며 첫 번째 열에서 세 번째 열까지 이어지도록 지시함

  ```css
  .my-element :first-child {
    grid-row: 1/3;
    grid-column: 1/4;
  }
  ```

  





##### ✏️Flow layout

- Inline block

  - 블록 레벨 요소의 일부 특성이 있지만 텍스트를 가진 박스를 얻을 수 있음

  ```css
  p span {
    display: inline block;
  }
  ```

- Floats

  - 지정된 방향으로 변환하도록 요소를 지정함

  ```css
  img {
    float: left;
    margin-right: 1em;
  }
  ```







##### ✏️Positioning

- 문서의 일반 흐름에서 요소가 작동하는 방식과 다른 요소와 관련된 방법을 변경

  ```css
  .my-element {
    position: relative;
    top: 10px;
  }
  ```

  > 이 요소는 문서에 있는 현재 위치를 기준으로 10px 아래도 밀림 *자신에 대해 상대적으로 위치하기 때문*

  - 요소에 `position: relative`를 추가하면 `position: absolute`를 가진 모든 하위 요소의 포함 블록이 됨

  ```css
  .my-element {
    position: relative;
    width: 100px;
    height: 100px;
  }
  
  .another-element {
  	position: absolute;
  	bottom: 0;
  	right: 0;
  	width: 50px;
  	height: 50px;
  }
  ```

  - `position`을 `absolute`로 설정하면 현재 문서 흐름에서 요소가 분리됨
    - 가장 가까운 상대 부모에서 `top`, `right`, `bottom`, `left`을 사용하여 원한느 위치에 요소 배치
    - 절대 요소를 둘러싼 모든 내용은 해당 요소가 남긴 나머지 공간을 채우기 위해 다시 표시됨



