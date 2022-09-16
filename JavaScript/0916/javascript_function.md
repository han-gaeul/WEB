### `JavaScript 함수`

***

- 호출

  - 함수의 이름을 괄호와 함께 코드 내에 적음

    ```js
    function myFunction() {
      alert('hello');
    }
    
    myFunction()
    // calls the function once
    ```

- 익명 함수

  - 이름이 없는 함수

  - 주로 이벤트 핸들러와 함께 사용됨

    ```js
    function() {
      alert('hello');
    }
    ```

  - 예

    ```js
    var myButton = document.querySelector('button');
    
    myButton.onclick = function() {
      alert('hello');
    }
    ```

    >함수 내의 코드가 관련된 버튼을 클릭함에 따라 작동
    >
    >`<button>` 요소를 필요로 함

  - 변수 속에 익명함수를 넣을 수 있음

    ```js
    var myGreeting = function() {
      alert('hello');
    }
    
    // 함수 호출
    myGreeting();
    ```

- 매개변수

  - 몇몇 함수는 호출을 위해 매개변수를 필요로 함

  - 함수 괄호 안에 포함될 필요가 있는 값으로, 올바르게 동작하기 위해서 필요

  - 예

    ```js
    // 브라우저 내장 함수인 Math.random()은 매개변수가 필요 없음
    var myNumber = Math.random();
    
    // 브라우저 내장 문자열 replace() 함수는 두 개의 매개변수를 필요로 함
    var myText = 'I am a string';
    var newString = myText.replace('string', 'sausage');
    ```

    - 선택 사항일 수도 있음. 즉, 명시해줄 필요가 없다는 뜻

    - 이런 경우 일반적으로 함수는 기본 기능을 수행함

      ```js
      // 예) 배열과 관련된 join() 함수의 매개변수
      var myArray = ['I', 'love', 'chocolate', 'frogs'];
      var madeAString = myArray.join(' ');
      // returns 'I love chocolate frogs'
      var madeAString = myArray.join();
      // returns 'I,love,chocolate,frogs'
      ```

- 스코프와 충돌

  - 스코프

    - 함수를 생성할 때, 변수 및 함수 내 정의된 코드들은 그들만의 분리된 '스코프' 안에 자리하게 됨
    - 즉, 다른 함수의 내부나 외부 함수의 코드가 접근할 수 없는 그들만의 구획에 갇혀 있다는 뜻
    - 전역 스코프(global scope) : 함수 바깥에 선언된 가장 상위 레벨의 스코프. 전역 스코프 내에 정의된 값들은 어느 코드든 접근이 가능함

  - 충돌

    - 외부 스크립트의 코드와 같은 변수 이름을 사용하면 충돌이 일어남

    - 예

      ```html
      <!-- Excerpt from my HTML -->
      <script src="first.js"></script>
      <script src="second.js"></script>
      <script>
        greeting();
      </script>
      ```

      ```js
      // first.js
      var name = 'Chris';
      function greeting() {
        alert('Hello ' + name + ': welcome to our company.');
      }
      ```

      ```js
      // second.js
      var name = 'Zaptec';
      function greeting() {
        alert('Our company is called ' + name + '.');
      }
      ```

      - 호출하고 싶은 두 함수 모두 `greeting()`이지만, 오직 `first.js` 파일의 `greeting()` 함수에만 접근할 수 있음. *(두번째 것은 무시 됨)*
      - `second.js` 파일에서 `let` 키워드로 `name` 변수를 두 번째로 선언하려고 시도하는 것은 오류를 발생시킴

- 함수 내부의 함수

  - 예

    ```js
    function myBigFunction() {
      var myValue;
    
      subFunction1();
      subFunction2();
      subFunction3();
    }
    
    function subFunction1() {
      console.log(myValue);
    }
    
    function subFunction2() {
      console.log(myValue);
    }
    
    function subFunction3() {
      console.log(myValue);
    }
    ```

    >`ReferenceError: MyValue is not definrd` 오류 발생
    >
    >왜냐하면 `myValue` 변수가 함수가 호출되는 같은 스코프 내에 정의되어 있지만
    >
    >이것은 함수 정의*(함수가 호출될 때 실행되는 실제 코드)* 내부에 정의되어 있지 않음

    ```js
    function myBigFunction() {
      var myValue = 1;
    
      subFunction1(myValue);
      subFunction2(myValue);
      subFunction3(myValue);
    }
    
    function subFunction1(value) {
      console.log(value);
    }
    
    function subFunction2(value) {
      console.log(value);
    }
    
    function subFunction3(value) {
      console.log(value);
    }
    ```

    >코드가 작동하게 하려면 값을 함수 내부에 매개변수로써 위와 같이 전달해야 함

  