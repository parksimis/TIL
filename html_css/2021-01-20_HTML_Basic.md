# HTML_Basic

## 1. HTML이란?

* HTML(HyperText Markup Language)
  * 웹 페이지를 위한 지배적인 마크업 언어(Wiki)
  * 웹페이지를 만드는 코드



## 2. HTML 요소

* HTML 문서는 완전한 HTML 요소로 구성되어 있고, HTML 요소의 가장 보편적인 형태는 세 가지 구성요소를 가진다.

1. 태그 한 쌍

   : "시작 태그(Start tag)와 종료 태그(End Tag)"와 같은 태그 한 쌍

2. 속성

   : 몇 가지 요소 속성은 그 태그들 내에서 특성을 부여한다.

3. 콘텐츠

   : 문자와 그래픽 정보 콘텐츠를 화면에 표시한다.



## 3. HTML 기본 문서 구조

* 태그(tag) : HTML에서 사용하는 명령어 (문자열 기호)
* 원하는 모양과 형태로 브라우저에게 명령을 내린다.
* 속성과 함께 사용할 수 있다.
* 태그 사용 형식
  * 대부분 시작 태그(`<태그명>`)와 종료 태그(`</태그명>`)를 함께 사용한다.
  * Ex. `<title> 문서 제목 </title>`
* 종료 태그 없이 혼자 사용하는 태그
  * `<br>` : 줄 바꿈
  * `<img>` : 이미지 삽입
  * `<hr>` : 수평선 삽입
* 태그는 대소문자 구별없이 사용이 가능하다.



#### -  HTML 기본 구조

```html
<!-- 현재 문서가 HTML5 언어로 작성된 웹문서임을 표기 -->
<!DOCTYPE html>
<html lang="en">
<!-- HEAD 부분 : 틀 부분, 브라우저의 외고각 또는 body를 꾸밀 내용들을 입력 -->
<head>
    <!-- 문자 인코딩 및 문서 키워드, 요약 정보 입력 -->
    <!-- title 태그가 오기 이전에 문자 인코딩 방식 선언해주는 것이 좋음 -->
    <!-- meta 문서 전체의 설정에 관한 내용 -->
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<!-- body 부분 : 본문 -> 실제 웹 브라우저 화면에 나타날 내용들 -->
<!-- 화면에 출력하고자 하는 모든 내용은 body 부분에 포함된다. -->
<body>
	<p>Hello World</p>
    <p>안녕하세요.</p>
</body>
</html>
```

* `<!DOCTYPE HTML>`
  * 문서의 첫 줄에 DTD(Document Type Definition) 선언을 적는 것.
  * 작성하는 문서가 HTML5임을 명시한다.

* `<html> </html>`

* 문서의 시작과 끝을 표시한다.

  * `lang='언어코드'` : 한국(ko), 영어(en) 
    * 검색엔진 및 브라우저 지원 목적으로 작성하는 속성으로 **웹접근성**을 위한 것이다.
    * 화면 낭독 프로그램(스크린 리더)가 이 언어를 인식해 자동으로 음성을 변환하거나, 해당 언어에 적합한 발음을 제공할 수 있도록 한다.
    * 또한, lang 설정과 접속자 크롬 브라우저의 언어 설정이 다른 경우, 크롬 자동 번역 인터페이스가 뜨게 설정할 수도 있다.

* `<head> </head>`

* 웹 브라우저 화면에는 보이지 않지만, 웹 브라우저가 알아두어야 할 문서 정보를 포함하고 있다. 

* 문서의 정보를 작성하는 부분

  * `<meta>`

  * 문자 인코딩 및 문서 키워드, 문서 정보들을 포함한다.

    * charset : 문자 인코딩이 되는 방식을 설정한다.

    ```html
    <meta charset = "utf-8">
    ```

  * `<link>`

    * 외부 리소스와 연결하는 태그

    ```html
    <link rel='relationship' href='외부문서파일 경로' type='해당 외부 문서 타입'>
    ```

  * `<title> </title>` 

  * 문서 제목 (크롬 탭에서 보이는 탭 이름이 나온다.)

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Title Name</title>
    </head>
    <body>
    
    </body>
    </html>
    ```

    ![title name](md-images/title%20name.PNG)

* `<body> </body>`

* 문서의 몸통 부분으로 실제 화면에 보이는 문서 내용을 포함한다.

* 대부분의 태그가 `<body>`와 `</body>` 사이에 위치한다.

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title Name</title>
  </head>
  <body>
  <body>
    <p>첫 번째 단락.</p>
    <p>두 번째 단락.</p>
  </body>
  </body>
  </html>
  ```

  * body 부분에 저렇게 작성하면, 아래와 같이 표시된다.

  ```markdown
  첫 번째 단락.
  
  두 번째 단락.
  ```

