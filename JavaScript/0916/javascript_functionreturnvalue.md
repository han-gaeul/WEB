### `JavaScript 함수 반환 값`

***

- 반환 값이란?

  - 함수가 완료 되었을 때 함수가 반환하는 값

  - 예

    ```js
    let myText = 'The weather is cold';
    let newString = myText.replace('cold', 'warm');
    console.log(newString);
    // 출력 : "The weather is warm"
    
    // replace() 문자열 함수는 문자열을 취해서,
    // 부분열(substring)을 다른 것으로 바꾸고,
    // 새로운 문자열을 반환합니다.
    ```

    >`replace()` 함수는 `myText` 문자열에서 호출되었고, 두 매개변수(parameter)를 전달 받았음 ➡︎ 교체된 문자열을 반환하고, 반환 값의 결과는 `newString`에 저장

- 사용자 정의 함수에서 반환 값 사용하기

  - 사용자 정의 함수에서 값을 반환하기 위해서는 `return` 키워드를 사용할 필요가 있음

  - 예

    - `draw()` 함수는 무작위의 원 100개를 HTML `<canvas>`에 그림

      ```js
      function draw() {
        ctx.clearRect(0, 0, WIDTH, HEIGHT);
        for (let i = 0; i < 100; i++) {
          ctx.beginPath();
          ctx.fillStyle = 'rgba(255,0,0,0.5)';
          ctx.arc(random(WIDTH), random(HEIGHT), random(50), 0, 2 * Math.PI);
          ctx.fill();
        }
      }
      ```

    - 각 반복 내에서 현재 원의 *x-coordinate*, *y-coordinate*, 그리고 *radius*에 대한 무작위 값을 생성하기 위해, `random()` 함수가 세 번 호출 됨

      `random()` 함수는 한 개의 매개변수를 가지고 `0`과 그 숫자 사이의 무작위 정수를 반환함

      ```js
      function random(number) {
        return Math.floor(Math.random() * number);
      }
      
      // 아래와 같이 작성도 가능
      function random(number) {
        const result = Math.floor(Math.random() * number);
        return result;
      }
      ```

    - 함수가 호출될 때마다 `Math.floor(Math.random() * number)` 계산의 결과가 반환되고 있음

      이 반환 값은 함수가 호출된 시점에서 나타나고, 코드는 계속됨

      그래서 다음을 실행했을 때,

      ```js
      ctx.arc(random(WIDTH), random(HEIGHT), random(50), 0, 2 * Math.PI);
      ```

      만약 세 개의 `random()` 호출이 각각 값 `500`, `200`, `35`를 반환했다면, 이 줄은 다음처럼 실행됨

      ```js
      ctx.arc(500, 200, 35, 0, 2 * Math.PI);
      ```

    - 함수 호출들이 먼저 실행되고, 실행되기 전에 함수의 반환 값이 함수 호출을 대신 함