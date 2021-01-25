# 공간 분할 태그

## 1) `<div>`

* block 형식으로 공간 분할
* 콘텐츠를 묶어 시각적 효과를 적용할 때 사용한다.
  * 본질적으로 아무것도 나타내지 않는 콘텐츠 영역을 설정함



## 2) `<span>`

* inline 형식으로 공간 분할



## 3) HTML5 시맨틱 구조 태그

* 시맨틱(Semantic)
  * 의미의, 의미론적인
  * 역할과 기능에 맞는 요소로 영역 구분
  * 각 요소가 의미가 있다는 것을 이야기함.

* HTML5 문서 구조

![](https://img1.daumcdn.net/thumb/R720x0.q80/?scode=mtistory2&fname=http%3A%2F%2Fcfile24.uf.tistory.com%2Fimage%2F2259F94D5651731A0FAB3C)

* 출처 : https://hunit.tistory.com/172

### - HTML5 시맨틱 구조의 특징

* HTML4로 만든 웹 문서의 결과 화면이나 HTML5로 만든 웬 문서의 결과 화면만 보면, **웹 브라우저에  보이는 모습은 동일**하지만, 실제로 웹 브라우저에서 **문서를 처리할 때 큰 차이**를 보인다.



### - HTML5 시맨틱 구조의 장점

* 소스만으로도 **문서 내용을 쉽게 이해**할 수 있다.
* **편리한 검색**이 가능하다.
* 뛰어난 **웹 접근성**을 가진다.
* 다양한 장치에 **통일된 결과**를 제공한다.

* 소스만으로도 문서 내용을 쉽게 이해할 수 있다.
  * 태그만 보고도 어느 부분이 **제목**이고, **메뉴**이고, 실제 **내용**인지 쉽게 구분할 수 있다.

* 편리한 검색
  * 사이트 검색 시 필요한 내용을 정확하게 찾을 수 있어 편리하다.
  * `<nav>` 태그 부분은 검색하지 않고, `<section>`이나 `<article>` 태그 부분만 찾아서 검색한다.



### - 문서 구조를 위한 HTML5 시맨틱 태그

* `<header>` : 머리말 지정
  * 헤더(제목)
  * 주로 페이지 맨 위쪽이나 왼쪽에 삽입한다.
  * **본문 중에 사용해 머리말로 쓸 수도 있다.**
* `<nav>` : 네비게이션(메뉴)
* `<section>` : 콘텐츠 (내용)
  * `<body>` 영역은 콘텐츠를 `<header>` / `<section>` / `<footer>`의 3가지 공간에 콘텐츠를 저장하는데, 그 중 본문 콘텐츠를 담고 있다.
  * 주제 별 영역, 문서의 일반적인 영역, 다른 주제와의 구분을 위해 사용한다.
  * `<section>` 안에 `<section>`을 넣는 것도 가능함.
* `<article>` : 콘텐츠 안의 내용
  * 실질적인 내용을 넣는다.
* `<aside>` : 사이드 바
  * 본문 이외의 내용을 담고 있는 시맨틱 태그
  * 본문 옆 광고 또는 링크를 달아 표현함

* `<footer>` 
  * 화면 구조 중 제일 아래에 위치
  * 회사 소개 / 저작권 / 약관 / 제작정보 등을 넣는 푸터 부분
  * 연락처는 `<address>` 태그를 사용하여 표시함.



### - 적용 예시

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>semantic tag 사용예제</title>
</head>
<body>
    <div id='wrap'>
        <header>
        	<div id='topMenu'>
            로그인 이벤트 장바구니 고객센터 회원가입
            </div>
        </header>
        <nav>
            <div id='menuBox'>메뉴</div>
            <div id='menuBox'>서브메뉴</div>
        </nav>
        <section>
            <article>
                <div id="slideShowBox">슬라이드쇼</div>
            </article>
            <article>
                <div id="content">메인 내용</div>
            </article>
        </section>
        <footer>
            <div id="info">회사정보/Copyright</div>
        </footer>
    </div>
</body>
</html>
```

* 위의 결과 자체로는 그냥 글자만 보이는 형태이다.
* 따라서 이후 css를 활용해 여러 스타일을 적용해 꾸밀 수 있다.