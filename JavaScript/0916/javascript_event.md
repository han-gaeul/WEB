### `JavaScript 이벤트`

***

- 이벤트란?

  - 프로그래밍하고 있는 시스템에서 일어나는 사건(action) 혹은 발생(occurrence)

  - 사용자가 원한다면 그것들에 어떠한 방식으로 응답할 수 있게 시스템이 말해주는 것

  - 예

    - 하나의 `<button>`을 가지고 있을 때, 이 버튼을 누르면 배경이 무작위의 색으로 바뀌게 함

      ```html
      <button>Change color</button>
      ```

      ```js
      const btn = document.querySelector('button');
      
      function random(number) {
        return Math.floor(Math.random() * (number+1));
      }
      
      btn.onclick = function() {
        const rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
        document.body.style.backgroundColor = rndCol;
      }
      ```

      >`Document.querySelector()` 함수를 사용하여, `btn` 상수 내부에 버튼에 대한 참조를 저장함. 또한, 무작위의 숫자를 반환하는 함수를 정의함.
      >
      >`btn` 상수는 `<button>` 요소를 가리키고, 이 타입의 객체는 발생시킬 수 있는 얼마간의 이벤트를 가지고 있으므로, 이벤트 핸들러를 사용 가능함
      >
      >`onclick` 이벤트 핸들러 프로퍼티를 무작위의 RGB 색상을 생성하고 그것과 같은 `<body> background-color`를 설정하는 코드를 포함하는 익명함수에 설정함으로써 `click` 이벤트 발생

- 웹 이벤트를 사용하는 방법들

  - 이벤트 핸들러 프로퍼티

    ```js
    const btn = document.querySelector('button');
    
    btn.onclick = function() {
      const rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
      document.body.style.backgroundColor = rndCol;
    }
    ```

    >`onclick` 프로퍼티는 이 상황에서 쓰이고 있는 이벤트 핸들러 프로퍼티
    >
    >본질적으로 버튼에서 사용 가능한 다른 것들과 같은 프로퍼티지만 어떤 코드와 동일한 것을 설정했을 때, 그 코드는 버튼에서 이벤트가 발생 되었을 때 실행 됨

  - 이벤트 핸들러를 추가하고 제거하기

    - 추가

    ```js
    const btn = document.querySelector('button');
    
    function bgChange() {
      const rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
      document.body.style.backgroundColor = rndCol;
    }
    
    btn.addEventListener('click', bgChange);
    ```

    > `addEventListener()` 함수 안에 두 매개변수(parameter)를 명시
    >
    > 이 핸들러에 등록하고자 하는 이벤트의 이름과 그것에 응답하여 실행하기를 원하는 핸들러 함수를 구성하는 코드
    >
    > `addEventListener()` 내부에, 다음과 같이 익명 함수 안에 모든 코드를 넣는 것도 가능

    ```js
    btn.addEventListener('click', function() {
      var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
      document.body.style.backgroundColor = rndCol;
    });
    ```

    - 제거

    ```js
    btn.removeEventListener('click', bgChange);
    ```

    > 이전에 추가한 이벤트 핸들러를 제거하는 `removeEventListener()`라는 함수가 있음
    >
    > 이것은 이 섹션의 첫번째 코드 블록 안에 있는 이벤트 핸들러를 제거
    >
    > 이벤트 핸들러는 `AbortSignal`을 `addEventListener()`에 전달하고, 나중에 `AbortSignal`을 소유하고 있는 컨트롤러에서 `abort()`를 호출함으로써 제거할 수도 있음

    ```js
    // AbortSignal로 제거할 수 있는 이벤트 핸들러 추가
    const controller = new AbortController();
    btn.addEventListener('click', function() {
      var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
      document.body.style.backgroundColor = rndCol;
    }, { signal: controller.signal });
    // 이 핸들러에 AbortSignal을 전달
    ```

    > 위의 코드로 생성된 이벤트 핸들러는 다음 코드로 제거할 수 있음

    ```js
    controller.abort();
    // 이 컨트롤러와 연관된 어떠한/모든 이벤트 핸들러를 제거
    ```

- 다른 이벤트 개념들

  - 이벤트 객체

    - 이벤트 핸들러 함수 내부에서 `event`, `evt`, `e`와 같은 이름으로 명명된 매개변수

    - 추가적인 기능과 정보를 제공하기 위해 이벤트 핸들러에 자동으로 전달됨

    - 예

      ```js
      function bgChange(e) {
        const rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
        e.target.style.backgroundColor = rndCol;
        console.log(e);
      }
      
      btn.addEventListener('click', bgChange);
      ```

      > 이벤트 객체 `e`를 함수에 포함하고 함수에서 배경 색상 스타일을 `e.target`에서 설정
      >
      > 이벤트 객체의 `target` 프로퍼티는 항상 이벤트가 발생된 요소에 대한 참조