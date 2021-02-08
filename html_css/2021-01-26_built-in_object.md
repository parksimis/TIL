# Built-in Object

자바스크립트의 객체 분류

![자바스크립트 객체 분류](https://poiemaweb.com/img/objects.png)

<center>자바스크립트 객체 분류</center>

## 1. Native Object(네이티브 객체)

* ECMAScript 명세에 정의된 객체를 말함.
* 애플리케이션 전역의 공통 기능을 제공
* 애플리케이션의 환경과 관계없이 언제나 사용 가능
* 네이티브 객체를 **Global Objects**라고 부르기도 하지만, **전역 객체(Global Object)**와는 다른 의미임.
  * 전역 객체 : 모든 객체의 최상위 객체를 의미, Browser-side에서는 `window`, Server-side(Node.js)에서는 `global` 객체를 의미

### 1) Object

* `Object()` 생성자 함수는 객체를 생성함.
* 생성자 인수가 null이거나 undefined인 경우 빈 객체를 반환
* 객체 생성 시 특수한 상황이 아니면 객체리터럴 방식을 사용하는 것이 일반적.



### 2) Function

* 자바스크립트의 모든 함수는 Function 객체이다.
* new 연산자를 사용해 생성 가능



### 3) Boolean

* 원시 타입 boolean을 위한 wrapper 객체이다.
* Boolean 생성자 함수로 Boolean 객체를 생성 가능



### 4) Number

* [Number](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number)

### 5) Math

* [Math](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math)

### 6) Date

* [Date](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date)

### 7) String

* [String](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)

### 8) RegExp

* [RegExp](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/RegExp)

### 9) Array

* [Array](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)

### 10) Error

* Error 생성자는 error 객체를 생성함.
* error 객체의 인스턴스는 런타임 에러가 발생시 throw 됨.
* 관련 객체
  * EvalError
  * InternalError
  * RangeError
  * ReferenceError
  * SyntaxError
  * TypeError
  * URIError

### 11) Symbol

* 유일하고 변경 불가능한(immutable)한 원시 타입



---



## 2. Host Object(호스트 객체)

* 브라우저 환경에서 제공하는 window, XMLHttpRequest, HTMLElement 등의 DOM 노드 객체와 같이 호스트 환경에 정의된 객체
* 브라우저에서 동작하는 환경의 호스트 객체는 전역 객체인 window, BOM(Browser Object Model), DOM(Document Object Model) 및 XMLHttpRequest 객체 등을 제공



### 1) 전역 객체(Global Object)

* 모든 객체의 유일한 최상위 객체
* Browser에서는 window, Sever에서는 global



### 2) BOM (Browser Object Model)

* 브라우저 객체 모델
  * 브라우저 탭 또는 브라우저 창의 모델을 생성
  * 최상위 객체(window) 현재 브라우저 창 또는 탭을 표현하는 객체
  * 객체의 자식 객체들은 브라우저의 다른 기능들을 표현
  * Standard Built-in Objects가 구성된 후에 구성됨

![BOM 구성요소](https://poiemaweb.com/img/BOM.png)



### 3) DOM (Document Object Model)

* 문서 객체 모델
  * 현재 웹페이지의 모델을 생성
  * 최상위 객체(document)는 전체 문서를 표현
  * 자식 객체들은 문서의 다른 요소들을 표현함.
  * Standard Built-in Objects가 구성된 후에 구성

![DOM의 구성요소](https://poiemaweb.com/img/DOM.png)





---

##### 출처

* [poeimaweb](https://poiemaweb.com/js-built-in-object)

* [MDN wdb docs](https://developer.mozilla.org/ko/)