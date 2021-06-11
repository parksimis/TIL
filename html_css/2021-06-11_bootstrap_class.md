# bootstrap

### - container(컨테이너)

* 레이아웃 최상위 요소로 다른 요소를 포함

* 사용 예제

  ```html
  <!-- 메타크기를 먼저 설정해놓고 사용함 -->
  <meta name="viewport" content="width=device-width, initial-scale=1">
  
  <div class="container bg-primary text-white">
  		<h1>Bootstrap</h1>
  		<p>Container</p>
  </div>
  <div class="container-fluid bg-danger text-white">
  		<h1>Bootstrap</h1>
  		<p>Container</p>
  </div>
  <div class="container">
  	<div class="jumbotron">
  		<h1>Jumbotron</h1>
  		<p>둥근 모서리 사각형 영역</p>
  	</div>
  </div>
  <div class="jumbotron">
  	<div class="container">
  		<h1>Jumbotron</h1>
  		<p>container 밖에 있는 jumbotron</p>
  	</div>
  </div>
  <div class="jumbotron jumbotron-fluid">
  	<div class="container">
  		<h1>Jumbotron jumbotron-fluid</h1>
  		<p>container 밖에 있는 jumbotron</p>
  	</div>
  </div>
  ```

  * `.container` : 반응형 고정폭 컨테이너
  * `.container-fluid` : 최대폭 컨테이너
  * `jumbotron` 
    * 일종의 대형 전광판
    * 특정 콘텐츠가 관심있는 정보를 눈에 띄게 보여주기 위한 큰 박스

  

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="UTF-8">
  		<meta name="viewport" content="width=device-width, initial-scale=1">
  		<title>Boostrap Jumbotron</title>
  		<link rel="stylesheet" href="css/bootstrap.min.css">
  		<script src="jquery-3.4.1.min.js"></script>
  		<script src="js/bootstrap.min.js"></script>	
  	</head>
  	<body>
  		<div class="container">
  	      <div class="jumbotron">
  		        <h1 class="text-center">K-digital 빅데이터 서비스 개발</h1>
  		        <p class="text-center">
  		        		MySQL / HTML / CSS / JavaScript / jQuery / Bootstrap /
  		        		Python / DJango</p>
  		        <p class="text-center">
  		        		<a class="btn btn-primary btn-lg" href="#">커리큘럼 보기</a></p>
  	      </div>
      </div>
  	</body>
  </html>
  ```

  * `.text-center / left / right` 
    * 텍스트 중앙, 좌(기본), 우 정렬
  * `.btn` (버튼 클래스)



### - Grid(그리드)

* 격자 모양으로 영역 분할 가능

* 1행을 12등분해서 비율로 배치

  * 행 : `class ="row"`
  * 열 : `class = "col-숫자"` (숫자 : 12칸 중에 해당하는 수)

* 윈도우 크기에 따라서 세로로 배치(반응형)
  * `col-scale-숫자` (숫자 : 12칸 중 차지하는 칸수)
  * `col-sm-숫자` 
    * 576px 이하면 세로로 배치
  * `col-md-숫자`
    * 768px 이하면 세로로 배치
  * `col-lg-숫자`
    * 992px 이하면 세로로 배치
  * `col-xl-숫자`
    * 1200px 이하면 세로로 배치
  * `col-숫자` : 가로방향으로 배치

* 사용 예제

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <title>Title</title>
      <link rel="stylesheet" href="css/bootstrap.min.css">
      <script src="js/jquery-3.4.1.min.js"></script>
      <script src="js/bootstrap.min.js"></script>
  </head>
  <body>
  <div class="container">
      <div class="row">
          <div class="col-6 bg-success">a</div>
          <div class="col-6 bg-warning">b</div>
      </div><br>
      <div class="row">
          <div class="col-2 bg-success">c</div>
          <div class="col-10 bg-warning">d</div>
      </div><br>
      <div class="row">
          <div class="col-4 bg-success">e</div>
          <div class="col-8 bg-warning">g</div>
      </div><br>
  <hr>
      <div class="row">
          <div class="col-sm-6 bg-success">a</div>
          <div class="col-sm-6 bg-warning">b</div>
      </div><br>
      <div class="row">
          <div class="col-md-6 bg-success">c</div>
          <div class="col-md-6 bg-warning">d</div>
      </div><br>
      <div class="row">
          <div class="col-lg-6 bg-success">e</div>
          <div class="col-lg-6 bg-warning">g</div>
      </div><br>
      <div class="row">
          <div class="col-lg-6 bg-success">e</div>
          <div class="col-lg-6 bg-warning">g</div>
      </div><br>
      <div class="row">
          <div class="col-xl-6 bg-success">e</div>
          <div class="col-xl-6 bg-warning">g</div>
      </div>
  </div>
  </body>
  </html>
  ```



## - 테이블

* `class="table"`

* `table-bordered` : 테두리 있음

* `table-borderless` : 테두리 없음

* `table-striped` : td 태그 흰색행/회색행

* `table-hover` : 행에 마우스를 올리면 색상 변경

* `table-dark` : 배경색을 검정색으로 설정

* `table-sm` / `table-md`

  * 행 간격 조정

* 사용예제

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="UTF-8">
  		<meta name="viewport" content="width=device-width, initial-scale=1">
  		<title>Boostrap Container</title>
  		<link rel="stylesheet" href="css/bootstrap.min.css">
  		<script src="jquery-3.4.1.min.js"></script>
  		<script src="js/bootstrap.min.js"></script>	
  	</head>
  	<body>
  		<div class="container">
  			<table class="table table-responsive-md table-hover table-warning">
  <!--				table-sm : 행 간격 조정-->
  				<thead class="thead-dark">
  				<tr>
  						<th>번호</th>
  						<th>제목</th>
  						<th>작성자</th>
  						<th>작성일</th>
  						<th>조회수</th>
  				</tr>
  				</thead>
  				<tr class="table-danger">
  						<td>4</td>
  						<td>HTML /CSS</td>
  						<td>flower</td>
  						<td>2019-11-17</td>
  						<td>2</td>
  				 </tr>
  				<tr>
  						<td>3</td>
  						<td>일본어 스터디</td>
  						<td>성춘향</td>
  						<td>2019-11-15</td>
  						<td>3</td>
  				 </tr>
  				<tr>
  						<td>2</td>
  						<td>Bootstrap</td>
  						<td>이몽룡</td>
  						<td>2019-11-12</td>
  						<td>0</td>
  				 </tr>
  				<tr>
  						<td>1</td>
  						<td>JSP 프로그래밍</td>
  						<td>홍길동</td>
  						<td>2019-11-07</td>
  						<td>1</td>
  				 </tr>				
  			</table>
  		</div>
  	</body>
  </html>
  ```

  

## - 버튼

* 버튼으로 사용할 요소에 `class="btn"`
* `<a>`, `<button>`, `<input type="button">` , `<input type="submit">`, `<input type="reset">` 등과 같은 태그들에 사용
* `class="btn btn-색상명"` : 색상 설정
* `btn-log / btn-md(default) / btn-sm` :  크기 설정
* `btn-outline-색상명` : 테두리 표시

* 사용 예제

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="UTF-8">
  		<meta name="viewport" content="width=device-width, initial-scale=1">
  		<title>Boostrap Button</title>
  		<link rel="stylesheet" href="css/bootstrap.min.css">
  		<script src="jquery-3.4.1.min.js"></script>
  		<script src="js/bootstrap.min.js"></script>	
  	</head>
  	<body>
  		<!-- btn만 설정 -->
  		<a class="btn" href="#">Link</a>
  		<button class="btn">Button</button>
  		<input class="btn" type="button" value="Input-Button">
  		<input class="btn" type="submit" value="Input-Submit">
  		<input class="btn" type="reset" value="Input-Reset">
  		
  		<hr>
  		
  		<!-- 색상 설정 -->
  		<a class="btn btn-primary" href="#">Link</a>
  		<button class="btn btn-warning">Button</button>
  		<input class="btn btn-success" type="button" value="Input-Button">
  		<input class="btn btn-danger" type="submit" value="Input-Submit">
  		<input class="btn btn-info" type="reset" value="Input-Reset">
  
  		<hr>
  		
  		<!-- 크기 설정 (md:디폴트) -->
  		<a class="btn btn-primary btn-lg" href="#">Link</a>
  		<button class="btn btn-warning btn-md">Button</button>
  		<input class="btn btn-success" type="button" value="Input-Button">
  		<input class="btn btn-danger btn-sm" type="submit" value="Input-Submit">
  		<input class="btn btn-info btn-sm" disabled="disabled" type="reset" value="Input-Reset">
  		
  		<hr>
  		
  		<a class="btn btn-outline-primary" href="#">Link</a>
  		<button class="btn btn-outline-dark">Button</button>
  		<input class="btn btn-outline-light text-dark" value="Input-Button">
  		<input class="btn btn-outline-danger" type="submit" value="Input-Submit">
  		<input class="btn btn-outline-info" type="reset" value="Input-Reset">
  	</body>
  </html>
  ```

  

* `d-flex` : css flex처리
* `justify-content-end` : 가로정렬, start, end