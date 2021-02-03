# 제어문(Control Flow)

* 주어진 조건에 따라 코드 블록을 실행(조건문)하거나 반복 실행(반복문)할 때 사용.
* 일반적으로 코드는 위에서 아래 방향으로 순차적으로 실행되는데, 제어문을 통해 이를 인위적으로 제어할 수 있다.



## 1. 블록문

* 블록문(Block statement / Compound statement)
  * 0개 이상의 statement를 중괄호로 묶은 것.
  * 자바스크립트는 블록문을 하나의 단위로 취급
  * 문의 끝에는 세미 콜론(;)을 붙이는 것이 일반적이지만, 블록문은 붙이지 않음



## 2. 조건문

* 조건문(conditional statement)
  * 주어진 조건식(conditional expression)의 평가 결과에 따라 코드 블럭(블럭문)의 실행을 결정.
    * 조건식 : Boolean 값으로 평가될 수 있는 표현식

### 1) if..else 문

* 주어진 조건식의 평가 결과(논리적 참, 거짓)에 따라 실행할 코드 블록을 결정함.
  * 조건식의 평가 결과가 Boolean 값이 아니면, Boolean 값으로 **강제 변환**되어 참, 거짓 구별

* 기본 형식

  ```javascript
  if (조건식) {
      // 참인 경우 실행되는 Block
  } else {
      // 거짓인 경우 실행되는 Block
  }
  ```

  * 조건식을 추가하고 싶은 경우 `else if`문을 사용

  ```javascript
  if (조건식1) {
      // 조건식 1이 참인 경우 실행되는 Block
  } else if (조건식2) {
      // 조건식 2가 참인 경우 실행되는 Block
  } else {
      // 조건식 1과 2과 모두 거짓이면 실행되는 Block
  }
  ```

  * `else`가 없이도 사용이 가능하다.
  * `if` , `else`는 한 번만 사용이 가능하지만, `else if`문은 여러번 사용이 가능하다.

### 2) switch 문

* switch 문의 표현식을 평가하여, 그 값가 일치하는 표현식을 갖는 case 문으로 실행 순서를 이동 시킴.

* case 문은 상황(case)을 의미하는 표현식을 지정 후 콜론(:)으로 마치고, 그 뒤에 실행할 문들을 위치시킴.

* 일치하는 case 문이 없다면 실행 순서는 default 문으로 이동함.(option)

* 기본 형식

  ```javascript
  switch (expression) {
      case expression1:
          switch 문의 expression과 expression1이 일치하면 실행될 statement;
          break;
      case expression1:
          switch 문의 expression과 expression2이 일치하면 실행될 statement;
          break;
      default:
          switch 문의 expression과 일치하는 expression을 갖는 case 문이 없을 때 실행되는 statement;
              
  }
  ```

  * switch 문의 표현식은 Boolean 값보다 문자열, 숫자 값인 경우가 많음.
  * `break`를 사용하지 않으면 코드는 순차적으로 실행됨. 따라서 `break`를 까먹지 말고 작성

## 3. 반복문

* 주어진 조건식(conditional expression)의 평가 결과가 참인 경우 조건식이 거짓이 될 때까지 코드 블럭을 반복적으로 실행

### 1) for 문

* 조건식이 거짓으로 판별될 때까지 코드 블록 반복 실행

* 기본 형식

  ```javascript
  for (초기화식; 조건식; 증감식) {
      조건식이 참인 경우 반복 실행될 statement;
  }
  ```

  * 초기화식, 조건식, 증감식을 모두 작성하지 않는 경우 무한 루프에 빠진다.



### 2) while 문

* 주어진 조건식 평가 결과가 참이면 코드 블록을 계속해서 반복 실행함. 
* 조건문의 평가 결과가 거짓이 되면 실행을 종료함.
* 조건식의 평가 결과가 언제나 참이면 무한루프가 되는데, 따라서 이를 탈출하기 위해서 코드 블럭 탈출 조건을 if문에 부여하고, break 문으로 코드 블럭을 탈출

```javascript
var count = 0;

// 무한루프
while (true) {
  console.log(count);
  count++;
  // count가 3이면 코드 블록을 탈출한다.
  if (count === 3) break;
} // 0 1 2
```

### 3) do...while 문

* `do...while`문은 코드 블록을 실행하고, 조건식을 평가함.(코드 블록은 무조건 한번 이상 실행됨)

```javascript
var count = 0;

// count가 3보다 작을 때까지 코드 블록을 계속 반복 실행한다.
do {
  console.log(count);
  count++;
} while (count < 3); // 0 1 2
```



### 4) break 문

* 반복문, 또는 switch 문의 코드 블록을 탈출함. 
* break 문은 반복문을 더 이상 진행하지 않아도 될 때 불필요한 반복을 피할 수 있어 유용



### 5) continue 문

* break 문처럼 반복문을 탈출하지 않고, 반복문의 코드 블록 실행을 현 시점에서 중단하고 반복문의 증감식으로 이동함.