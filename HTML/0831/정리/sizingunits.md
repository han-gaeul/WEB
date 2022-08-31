### `CSS 배우기 - Sizing Units`

***

- 숫자

```css
p {
  font-size: 24px;
  line-height: 1.5;
}
```

> 예에서 `1.5`의 150%에 상당함

- 퍼센티지

  - 예) `width`는 부모 요소의 사용 가능한 폭에 대한 비율로 계산 됨

  ```css
  dic {
    width: 300px;
    height: 100px;
  }
  div p {
    width: 50%;
  }
  ```

- 치수 및 길이

  - 절대 길이

    - 예) `cm` 요소의 크기를 조정하고 인쇄하려면 눈금자와 비교해도 정확해야 함

    ```css
    div {
      width: 10cm;
      height: 5cm;
      background: black;
    }
    ```

    | 구성 단위 | 이름                               | 등가                |
    | --------- | ---------------------------------- | ------------------- |
    | cm        | Centimeters(센티미터)              | 1cm = 96px/2.54     |
    | mm        | Millimeters(밀리미터)              | 1mm = 1/10th of 1cm |
    | Q         | Quarter-millimeters(쿼터 밀리미터) | 1Q = 1/40th of 1cm  |
    | in        | Inches(인치)                       | 1in = 2.54cm = 96px |
    | pc        | Picas(피카스)                      | 1pc = 1/6th of 1in  |
    | pt        | Points(포인트)                     | 1pt = 1/72th of 1in |
    | px        | Pixels(픽셀)                       | 1px = 1/96th of 1in |

  - 상대 길이

    - 글꼴 크기 상대 단위

    | 구성 단위 |                                                              |
    | --------- | ------------------------------------------------------------ |
    | em        | 글꼴 크기에 비해 1.5em은 부모의 기본 계산된 글꼴 크기보다 50% 더 커짐 |
    | ex        | 요소의 현재 계산된 글꼴 크기에서 x-높이, 문자 'x' 또는 '.5em' 중<br> 어느 것을 사용할지 결정하는 접근 |
    | cap       | 요소의 현재 계산된 글꼴 크기에서 대문자의 높이               |
    | ch        | 요소의 글꼴에서 좁은 글리프의 평균 문자 이동                 |
    | ic        | 요소 글꼴의 전체 너비 글리프의 평균 문자 이동                |
    | rem       | 루트 요소의 글꼴 크기 (기본값은 16px)                        |
    | lh        | 요소의 회선 높이                                             |
    | rlh       | 루트 요소의 라인 높이                                        |

    <img src="sizingunits.assets/size.png" alt="size" style="zoom:50%;" /

- Miscellaneous units(기타 단위)

  - Angle units(각도 단위)
    - `deg` 각도 단위를 사용하여 중심축에서 `div`를 90도 회전할 수 있음

  ```css
  div {
    width: 150px;
    height: 150px;
    transform: rotate(60deg);
  }
  ```

  - Resolution units(해상도 단위)
    - 아래의 예시에서 `min-resolution` 값은 `192dpi`이다. *(dpi 단위는 인치당 도트를 나타냄)*

  ```css
  @media (min-resolution: 192dpi) {
    div {
      background-image: url('a-high-resolution-image.jpg');
    }
  }
  ```

  

