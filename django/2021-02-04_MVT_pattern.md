# 장고에서의 애플리케이션 개발 방식

웹사이트 설계 시 가장 먼저 해야 할 일은 프로그램이 해야 할 일을 적당한 크기로 나누어서 모듈화 하는것이다. 이 경우, 웹사이트의 전체 프로그램 또는 모듈화된 단위 프로그램을 애플리케이션이라고 함. 즉, **프로그램으로 코딩할 대상**을 <u>애플리케이션</u>이라고 부름

* 장고에서의 용어

  장고에서는 이 애플리케이션의 개념을 웹 서버 측면에서 좀 더 구체화하고 있음.

  * 프로젝트(Project) : 웹 사이트에 대한 전체 프로그램
  * 애플리케이션(Application) : 모듈화된 단위 프로그램

  -> 애플리케이션 프로그램들이 모여 프로젝트를 개발한다는 개념



## 1. MVT 패턴

* 일반적으로 웹 프로그램 개발 시 언급되는 MVC(Model-View-Controller) 패턴이란, 데이터(Model), 사용자 인터페이스(View), 데이터를 처리하는 로직(Controller)을 구분해서 한 요소가 다른 요소들에 영향을 주지 않도록 설계하는 방식

* 이런 방식은 UI 디자이너 입장에서 **데이터 관리나 애플리케이션 로직에 신경 쓰지 않고**도 화면 UI 설계 가능

* 개발자도 화면 디자인은 디자이너에게 맡기고 **자신의 설계 및 개발 업무에 집중 가능**

* 장고도 위의 개념을 그대로 받아들였지만, 용어(MVT)는 다르게 사용함.

* 장고의 MVT 패턴

  | MVC 패턴에서의 역할 | MVT 패턴에서의 역할 |
  | ------------------- | ------------------- |
  | Model               | Model               |
  | View                | Template            |
  | Controller          | View                |

  

[![장고의 MVT 패턴](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpdQ3m%2FbtqwhTpC3gU%2FvXB2IGfXViX7cGFQgXjlR1%2Fimg.png)](https://butter-shower.tistory.com/49)

<center><small>장고의 MVT 패턴</small></center>

* MVT 패턴의 처리 과정
  1. 클라이언트로부터 요청을 받으면 **URL conf**를 이용해 URL을 분석
  2. URL 분석 결과를 통해 해당 URL에 대한 처리를 담당할 **뷰**를 결정
  3. 뷰는 자신의 로직을 실행하면서, 만일 DB 처리가 필요하면 **모델**을 통해 처리하고 그 결과를 반환받음
  4. 뷰는 자신의 로직 처리가 끝나면 **템플릿**을 사용하여 클라이언트에 전송할 HTML 파일을 생성
  5. 뷰는 최정 결과로 HTML 파일을 클라이언트에게 보내 응답



## 2. Model - 데이터베이스 정의

* Model : 사용될 데이터에 대한 정의를 담고 있는 장고의 클래스

* 장고는 ORM 기법을 사용해 애플리케이션에서 사용할 데이터베이스를 클래스로 매핑해 코딩

  * 하나의 모델 클래스는 하나의 테이블에 매핑, 모델 클래스의 속성은 테이블의 컬럼에 매핑

* 모델 클래스는 `models.py` 파일에 정의

* 예시

  ```python
  # Question 모델(테이블) 생성
  ## 각 테이블을 출력할 때 사용할 대표 필드 선언
  class Question(models.Model):
      # id 필드는 django의 모델이 자동 생성하기 때문에 생략 가능
      # 아무것도 표현 안하면 NOT NULL이 기본
      question_text = models.CharField(max_length=200)
      pub_date = models.DateTimeField('date published')
      # 생성 시 생성시각
  
      # 대표 필드 선택
      def __str__(self):
          return self.question_text
  ```

  * Primary Key는 클래스에서 정의하지 않아도 장고에서 자동으로 부여함.(직접 지정도 가능)

  

## 3. URLconf - URL 정의

클라이언트로부터 요청을 받으면 장고는 가장 먼저 요청에 들어있는 URL을 분석함. (요청에 들어있는 URL이 `urls.py` 파일에 정의된 URL 패턴과 매칭되는지 분석)

* 파이썬은 우아한(Elegant) URL 설계 지원(자바나 PHP 계열의 URL보다 직관적이고 이해가 쉬움)
* `urls.py` 파일에 URL과 처리 함수(View)를 매핑하는 파이썬 코드 작성

* 웹 클라이언트가 웹 서버에 페이지 요청 시, 장고에서 **URL 분석 순서**

  1. `settings.py` 파일의 ROOT_URLCONF 항목을 읽어 URLconf(urls.py)의 위치를 알아냄.
  2. URLconf를 로딩해 urlpatterns 변수에 지정되어 있는 URL 리스트 검사
  3. 위에서 순서대로 IRL 리스트 내용 검사하면서, URL 패턴이 매치되면 검사 종료
  4. 매치된 URL의 뷰 호출(View - 함수 또는 클래스의 메소드) 호출 시 HttpRequest 객체와 매칭할 때 추출된 단어들을 뷰에 인자로 넘겨줌.
  5. URL 리스트를 끝까지 검사했는데도 매칭 실패하면, 에러 처리 뷰 호출

* 예시

  ```python
  from django.urls import path
  from polls import views
  
  urlpatterns = [
      path('', views.index, name='index'), # 서버주소/polls/
      #path('polls/', views.index, name='index')로 정의시
      ## 서버주소:8000/polls/polls로 인식하므로 비워줘야함.
      path('<int:question_id>/', views.detail, name='detail'), # 서버주소/polls/<질문 id>
      path('<int:question_id>/results', views.results, name='results'), # 서버주소/polls/<질문 id>/results
      path('<int:question_id>/vote', views.vote, name='vote'), # 서버주소/polls/<질문 id>/vote
  ]
  ```

  * 꺽쇠 부분을 장고에서는 **Path Converter**라 부름

  * Path Converter 타입

    * `str` : /(슬래시)를 제외한 모든 문자열과 매치, 타입 지정되지 않으면 디폴트로 str 타입 사용
    * `int` : 0 또는 양의 정수와 매치
    * `slug` : slug 형식의 문자열(ASCII, 숫자, 하이픈, 밑줄로만 구성)과 매치
    * `uuid` : UUID 형식의 문자열과 매치.
    * `path` : /(슬래시)를 포함한 모든 문자열과 매치(URL 패턴의 일부가 아닌 전체를 추출하고자 할 때 많이 사용)

    

## 4. View - 로직 정의

* 장고는 웹 요청에 있는 URL 분석 후에 그 결과로 해당 URL에 매핑된 뷰를 호출함.
* View의 역할 
  1. 웹 요청을 받아 DB 접속 등 해당 애플리케이션의 로직에 맞는 처리 
  2.  1의 결과 데이터를 HTML로 변환하기 위해 템플릿 처리
  3. 최종 HTML로 된 응답 데이터를 웹 클라이언트로 반환
* 뷰는 함수 또는 클래스의 메소드로 작성, 웹 요청을 받고 응답을 반환함.
  * 응답은 HTML 데이터, 리다이렉션 명령, 404 에러 메시지 등이 있음.
* 일반적으로 `views.py` 파일에 작성하지만, 다른 파일에 작성해도 됨.





## 5. Template - 화면 UI 정의

* 장고가 클라이언트에게 반환하는 최종 응답 ==> HTML 텍스트

* 개발자가 응답에 사용할 `*.html`(템플릿) 파일을 작성, 장고가 이를 해석해 최종 HTML 텍스트 응답 생성 및 클라이언트에게 보냄.

  * 클라이언트는 응답으로 받은 HTML 텍스트를 해석해 웹 브라우저 화면에 UI를 보여줌

* 장고는 자체 템플릿 엔진을 갖고 있어 디자이너도 쉽게 이해할 수 있는 문법을 제공.

  -> 디자이너와 개발자 간에 협업이 편리해짐.

* 템플릿 파일은 `*.html` 확장자를 가지며, 장고의 템플릿 시스템 문법에 맞게 작성함.

* 유의할 점은 **템플릿 파일을 적절한 디렉토리에 위치시켜야 함.**

  * 템플릿 파일을 찾을 때는 `settings.py`의 `TEMPLATES` 및 `INSTALLED_APPS`에 지정된 앱의 디렉터리를 검색

  ```python
  # Application definition
  
  INSTALLED_APPS = [
      'django.contrib.admin',
      'django.contrib.auth',
      'django.contrib.contenttypes',
      'django.contrib.sessions',
      'django.contrib.messages',
      'django.contrib.staticfiles',
      'bookmark',
      'polls.apps.PollsConfig',
  ]
  
  
  TEMPLATES = [
      {
  		...
          'DIRS': [], # 비어있는 경우 app/templates/앱_이름/*.html
          ...
          
          },
  ]
  ```

  * `TEMPLATES` 항목에 정의된 디렉토리를 먼저 찾고, 그 다음에 `INSTALLED_APPS` 항목에 등록된 각 앱의 templates 디렉토리를 찾음.

  

## . MVT 코딩 순서

* Model, View, Template 중에서 무엇을 먼저 코딩해야한다는 순서는 없음.
* 화면 설계는 뷰와 템플릿 코딩으로 연결되고, 테이블 설계는 모델 코딩에 반영됨.
* 따라서 독립적으로 개발할 수 있는 모델을 먼저 코딩, 뷰와 템플릿은 서로 영향을 미치므로 모델 이후에 같이 작업하는 것이 일반적
* 자신만의 코딩 순서를 정하는 것이 로직을 풀어나가는 데 일관성을 유지할 수 있다. 



