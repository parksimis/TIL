# css 박스모델

## - 박스모델

HTML의 엘리먼트들은 박스의 형태를 가지고 있다. 이를 가리켜 박스모델이라고 하고, 박스의 크기와 박스 간의 간격을 정의하는 다양한 속성이 존재함.

## - 박스모델의 속성

![Boxmodel](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1/103.gif)

<div style="text-align:center; font-size:smaller;">출처 : <a href=https://opentutorials.org/course/1566/6>생활코딩-박스모델</a></div>

* margin : border를 기준으로 박스의 여백을 지정(시각적인 요소 없음)
* border : 박스의 테두리
* padding : 테두리외 content 간의 간격
* content : element 안에 포함되는 content

### margin(마진)

* 엘리먼트와 엘리먼트 간의 여백을 의미한다.
* 위 아래에 인접한 엘리먼트 간에는 margin의 값이 더 큰 쪽의 margins이 적용됨(좌우 아님)

### border(보더), 테두리

* 엘리먼트의 테두리를 의미함.
* margin과 padding의 경계가 됨.
* 테두리의 굵기와 색상의 스타일을 지정할 수 있다.

### padding(패딩)

* 테두리와 컨텐츠 간의 여백을 의미한다.

### content(콘텐츠)

* 엘리먼트 안에 포함되는 콘텐츠를 의미한다.
  * Ex. `<div> test </div>` 일 때, `div` 엘리먼트의 content는 test임
* content는 폭(width)과 높이(height)를 지정할 수 있다.



## - 박스 모델의 종류

* 블록 레벨 엘리먼트(block-level element)
  * 한 줄에 하나의 엘리먼트만 표시되는 종류의 엘리먼트
  * 다른 인라인 엘리먼트 뿐 아니라 블록 레벨 엘리먼트도 콘텐츠로 포함할 수 있다.
  * 특징
    * 행으로 배치 되고, 옆으로 나란히 배치 되지 않는다.
    * 여백이 존재한다.
  * 종류
    * `<div> / <h1> ~ <h6> / <form> / <ul> / <li> / <address> / <blockquote> / <table> / <hr>` 등
* 인라인 엘리먼트(inline element)
  * 한 줄에 여러 개의 엘리먼트가 표시되는 종류의 엘리먼트
  * 인라인 엘리먼트만 포함할 수 있고, 블록 레벨 엘리먼트의 자식이어야 한다.
  * 특징
    * 옆으로 나란히 배치 된다.
    * 여백 없이 내용물 만큼만 공간을 차지한다.
  * 종류
    * `<a> / <img> / <em> / <strong>` 등

* `display` 속성을 이용해서 블록레벨 엘리먼트를 인라인 엘리먼트로 변경할 수 있다.(반대의 경우도 가능)
* inline-block
  * 인라인, 블록 성격 모두를 포함
* display 속성을 활용한 변경

![Display properties](https://support.cohesiondx.com/sites/default/files/images/apply-styles/display-diagram-type-as-shape.svg)

<div style="text-align:center; font-size:smaller;">출처 : <a href=https://support.cohesiondx.com/5.4/user-guide/display-properties/>Display properties</a></div>

* display 속성의 값을 none으로 하면 엘리먼트를 화면에서 보이지 않게 할 수 있다.

## - float

* 해당 요소를 떠있게 만드는 속성, 기본 레이아웃 흐름에서 벗어나 왼쪽이나 오른쪽으로 이동하는 것을 의미한다.
* 엘리먼트를 원하는 위치로 이동시키고, 엘리먼트 뒤에 따라오는 엘리먼트들이 엘리먼트를 피해서 표시되도록 한다.
* float는 원래 이미지를 둘러싸고 흘러가는 텍스트를 표시하기 위해 고안되었다.
* 레이아웃을 구성할 때 사용 가능
* flaot 해제를 위해서는 clear 속성 사용



* 사용 예제

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>inlineBlock 예제</title>
      <style type="text/css">
          /* display 속성이 생략되면 default는 block이다.-> 행으로 배치/여백있음 */
          .greenBox {
              /*display: block;*/ /* default */
              /*display: inline;*/
              /*display 속성 값이 inline인 경우 width, height 속성은 적용되지 않는다.
              옆으로 배치되면서 내용만큼만 공간을 차지한다. */
              /*display: inline-block;*/
              /*옆으로 배치되는 inline 속성과 width, height 속성이 적용되는 block 속성을 결합한 형태이다.*/
              float : left;
              width: 150px;
              height: 75px;
              margin: 10px;
              border: solid 3px #73AD21;
          }
      </style>
  </head>
  <body>
      <h2> display 속성 (block/inline/inline-block)</h2>
      <div class="greenBox">박스 1</div>
      <div class="greenBox">박스 2</div>
      <div class="greenBox">박스 3</div>
      <div class="greenBox">박스 4</div>
  </body>
  </html>
  ```