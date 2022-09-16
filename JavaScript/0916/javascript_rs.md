### `JavaScript 반복문`

***

- 표준 문법

  ```html
  <script>
  for (초기화식; 종료 조건; 증감식) {
    // 실행할 코드
  }
  </script>
  ```

  - 초기화식 : 보통 숫자로 설정된 변수. 반복문이 실행될 횟수까지 증가. 카운터 변수라고도 함

  - 조건식 : 반복문이 언제 반복을 멈춰야만 하는지를 정의. 일반적으로 비교 연산자를 특징으로 하는 표현식. 종료 조건이 충족 되었는지를 확인하는 테스트

  - 증감식 : 반복문이 전체 반복을 거쳤을 때마다 항상 실행됨. 보통 카운터 변수를 증가시키기 위해 조건이 더 이상 `true`가 아닌 지점에 가까워지게 하기 위함

  - 예

    ```html
    <script>
    const cats = ['Bill', 'Jeff', 'Pete', 'Biggles', 'Jasmin'];
    let info = 'My cats are called ';
    const para = document.querySelector('p');
    
    for (let i = 0; i < cats.length; i++) {
      info += cats[i] + ', ';
    }
    
    para.textContent = info;
    </script>
    ```

- `break`

  - 즉시 반복문을 종료하고 브라우저가 반복문 뒤에 있는 코드로 이동하게 됨
  
  - 예
  
    ```html
    <label for="search">Search by contact name: </label>
    <input id="search" type="text">
    <button>Search</button>
    
    <p></p>
    ```

    ```html
    <script>
    const contacts = ['Chris:2232322', 'Sarah:3453456', 'Bill:7654322', 'Mary:9998769', 'Dianne:9384975'];
    const para = document.querySelector('p');
    const input = document.querySelector('input');
    const btn = document.querySelector('button');
    
    btn.addEventListener('click', function() {
      let searchName = input.value;
      input.value = '';
      input.focus();
      for (let i = 0; i < contacts.length; i++) {
        let splitContact = contacts[i].split(':');
        if (splitContact[0] === searchName) {
          para.textContent = splitContact[0] + '\'s number is ' + splitContact[1] + '.';
          break;
        } else {
          para.textContent = 'Contact not found.';
        }
      }
    });
    </script>
    ```
  
- `continue`

  - 반복문을 완전히 탈출하지 않고 반복문의 다음 반복으로 건너뜀
  
  - 예
  
    ```html
    <script>
    let num = input.value;
    
    for (let i = 1; i <= num; i++) {
      let sqRoot = Math.sqrt(i);
      if (Math.floor(sqRoot) !== sqRoot) {
        continue;
      }
    
      para.textContent += i + ' ';
    }
    </script>
    ```
  
- `while`, `do ... while`

  - `while`
  
    ```html
    초기화식
    while (종료 조건) {
      // 실행할 코드
    
      증감식
    }
    ```
  
    - 예
  
    ```html
    <script>
    let i = 0;
    
    while (i < cats.length) {
      if (i === cats.length - 1) {
        info += 'and ' + cats[i] + '.';
      } else {
        info += cats[i] + ', ';
      }
    
      i++;
    }
    </script>
    ```
  
  - `do ... while`
  
    ```html
    초기화식
    do {
      // 실행할 코드
    
      증감식
    } while (종료 조건)
    ```
  
    - 예
  
    ```html
    <script>
    let i = 0;
    
    do {
      if (i === cats.length - 1) {
        info += 'and ' + cats[i] + '.';
      } else {
        info += cats[i] + ', ';
      }
    
      i++;
    } while (i < cats.length);
    </script>
    ```
  
    
  
  

