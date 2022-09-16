### `JavaScript 조건문`

***

- `if ... else문`

  - 기본 문법

    ```html
    <script>
      if (조건) {
        조건이 참일 경우 실행할 코드
      } else {
        조건이 참이 아닌 경우 실행할 코드
      }
    </script>
    ```

    ```html
    <!-- else와 두 번째 중괄호를 포함하지 않아도 됨 -->
    <script>
      if (조건) {
        조건이 참일 경우 실행할 코드
      }
      
      <!-- 조건문에 의해서 제어되지 않기 때문에 항상 동작 -->
      실행할 다른 코드
    </script>
    ```

  - 짧은 문법

    ```html
    <script>
      if (조건) 조건이 참일 경우 실행할 코드
      else 조건이 참이 아닌 경우 실행할 코드
    </script>
    ```

    > 하지만 사용하는 것은 추천하지 않음

- `else if`

  - `if() {...}`와 `else {...}` 사이에 넣을 추가적인 블록

  - 예시

    ```html
    <label for="weather">Select the weather type today: </label>
    <select id="weather">
      <option value="">--Make a choice--</option>
      <option value="sunny">Sunny</option>
      <option value="rainy">Rainy</option>
      <option value="snowing">Snowing</option>
      <option value="overcast">Overcast</option>
    </select>
    
    <p></p>
    ```

    ```html
    <script>
    const select = document.querySelector('select');
    const para = document.querySelector('p');
    
    select.addEventListener('change', setWeather);
    
    function setWeather() {
      const choice = select.value;
    
      if (choice === 'sunny') {
        para.textContent = 'It is nice and sunny outside today. Wear shorts! Go to the beach, or the park, and get an ice cream.';
      } else if (choice === 'rainy') {
        para.textContent = 'Rain is falling outside; take a rain coat and a brolly, and don\'t stay out for too long.';
      } else if (choice === 'snowing') {
        para.textContent = 'The snow is coming down — it is freezing! Best to stay in with a cup of hot chocolate, or go build a snowman.';
      } else if (choice === 'overcast') {
        para.textContent = 'It isn\'t raining, but the sky is grey and gloomy; it could turn any minute, so take a rain coat just in case.';
      } else {
        para.textContent = '';
      }
    }
    </script>
    ```

- `if ... else 중첩`

  - `if ... else문`을 또 다른 조건문 안에 넣는 것

    ```html
    <script>
    if (choice === 'sunny') {
      if (temperature < 86) {
        para.textContent = 'It is ' + temperature + ' degrees outside — nice and sunny. Let\'s go out to the beach, or the park, and get an ice cream.';
      } else if (temperature >= 86) {
        para.textContent = 'It is ' + temperature + ' degrees outside — REALLY HOT! If you want to go outside, make sure to put some suncream on.';
      }
    }
    </script>
    ```

- 비교 연산자

  - 조건문 안의 조건을 테스트하는데 사용

    - `===`, `!==` : 한 값이 다른 값과 같거나 다른지 테스트
    - `<`, `>` : 한 값이 다른 값보다 작은지 큰지 테스트
    - `<=`, `>=` : 한 값이 다른 값보다 작거나 같은지, 크거나 같은지 테스트

  - 어떠한 값들이든 `false`, `undefined`, `null`, `0`, `NaN`이나 빈 문자열 (`''`)이 아닌 값은 조건문으로 테스트 되었을 때 `true`를 리턴

    ```html
    <script>
    let cheese = 'Cheddar';
    
    if (cheese) {
      console.log('Yay! Cheese available for making cheese on toast.');
    } else {
      console.log('No cheese on toast for you today.');
    }
    </script>
    ```

    ```html
    <script>
    let shoppingDone = false;
    let childsAllowance;
    
    if (shoppingDone) { // 명시적으로 '=== true'를 명시할 필요가 없습니다
      childsAllowance = 10;
    } else {
      childsAllowance = 5;
    }
    </script>
    ```

- 논리 연산자

  - 중첩된 `if ... else`문을 작성 없이 다양한 조건을 테스트 할 수 있음

    - `&&` : AND. 두 개 혹은 그 이상의 표현식이 개별적으로 `true`로 평가되게 식들을 같이 연결
    - `||` : OR. 하나 혹은 그 이상의 표현식이 개별적으로 `true`로 평가되게 두 개 혹은 그 이상의 식들을 같이 연결

  - 예

    ```html
    <!-- AND -->
    <script>
    if (choice === 'sunny' && temperature < 86) {
      para.textContent = 'It is ' + temperature + ' degrees outside — nice and sunny. Let\'s go out to the beach, or the park, and get an ice cream.';
    } else if (choice === 'sunny' && temperature >= 86) {
      para.textContent = 'It is ' + temperature + ' degrees outside — REALLY HOT! If you want to go outside, make sure to put some suncream on.';
    }
    </script>
    ```

    >첫 번째 코드 블록은 `choice === 'sumnny'`와 `temperature < 86`가 오직 `true`를 리턴해야만 실행됨

    ```html
    <!-- OR -->
    <script>
    if (iceCreamVanOutside || houseStatus === 'on fire') {
      console.log('You should leave the house quickly.');
    } else {
      console.log('Probably should just stay in then.');
    }
    </script>
    ```

    ```html
    <!-- NOT(!) -->
    <script>
    if (!(iceCreamVanOutside || houseStatus === 'on fire')) {
      console.log('Probably should just stay in then.');
    } else {
      console.log('You should leave the house quickly.');
    }
    </script>
    ```

    >`true`를 리턴한다면, `!`를 통해 전체 표현식이 `false`를 리턴하게 함

- `switch문`

  - 입력으로 하나의 표현식/값을 받고, 값과 일치하는 하나를 찾을 때까지 여러 항목을 살펴보고 그에 맞는 코드를 실행

    ```html
    <script>
    switch (expression) {
      case choice1:
        run this code
        break;
    
      case choice2:
        run this code instead
        break;
    
      // case
    
      default:
        actually, just run this code
    }
    </script>
    ```

  - 예

    ```html
    <label for="weather">Select the weather type today: </label>
    <select id="weather">
      <option value="">--Make a choice--</option>
      <option value="sunny">Sunny</option>
      <option value="rainy">Rainy</option>
      <option value="snowing">Snowing</option>
      <option value="overcast">Overcast</option>
    </select>
    
    <p></p>
    ```

    ```html
    <script>
    const select = document.querySelector('select');
    const para = document.querySelector('p');
    
    select.addEventListener('change', setWeather);
    
    
    function setWeather() {
      const choice = select.value;
    
      switch (choice) {
        case 'sunny':
          para.textContent = 'It is nice and sunny outside today. Wear shorts! Go to the beach, or the park, and get an ice cream.';
          break;
        case 'rainy':
          para.textContent = 'Rain is falling outside; take a rain coat and a brolly, and don\'t stay out for too long.';
          break;
        case 'snowing':
          para.textContent = 'The snow is coming down — it is freezing! Best to stay in with a cup of hot chocolate, or go build a snowman.';
          break;
        case 'overcast':
          para.textContent = 'It isn\'t raining, but the sky is grey and gloomy; it could turn any minute, so take a rain coat just in case.';
          break;
        default:
          para.textContent = '';
      }
    }
    </script>
    ```

- 삼항연산자

  - 조건을 테스트하고 만약 조건이 `true`라면 하나의 값/표현식을 리턴하고,

    만약 `false`라면 다른 값/표현식을 리턴하는 구문

    ````html
    <script>
    let greeting = ( isBirthday ) ? 'Happy birthday Mrs. Smith — we hope you have a great day!' : 'Good morning Mrs. Smith.';
    </script>
    ````

    >`isBirthday`라는 변수가 `true`라면, 게스트에게 생일 메시지를 보냄
    >
    >만약 아니라면, 게스트에게 일반적인 메시지를 보냄

  - 예

    ```html
    <label for="theme">Select theme: </label>
    <select id="theme">
      <option value="white">White</option>
      <option value="black">Black</option>
    </select>
    
    <h1>This is my website</h1>
    ```

    ```html
    <script>
    const select = document.querySelector('select');
    const html = document.querySelector('html');
    document.body.style.padding = '10px';
    
    function update(bgColor, textColor) {
      html.style.backgroundColor = bgColor;
      html.style.color = textColor;
    }
    
    select.onchange = function() {
      ( select.value === 'black' ) ? update('black','white') : update('white','black');
    }
    </script>
    ```

    