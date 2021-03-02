# 데이터 입력과 출력

## - 데이터 입력과 출력

### 1. R에서의 입력과 출력

```R
> no <- c(1,2,3,4)
> no
[1] 1 2 3 4
# 변수명을 실행하면 안의 값을 출력해줌 
# 이외에도 print(), cat() 함수로 사용 가능(아래에 후술)

```



### 2. 화면에서 데이터 입력받기

* 팝업창을 통해 화면에서 어떤 값을 입력받기 위해서는 `svDialogs` 패키지를 설치해, `dlgInput()`를 사용해야 함.

```R
# 화면에서 데이터 입력 받기
install.packages('svDialogs') # 패키지 설치 명령어(아래의 Pacakges > Install 에서도 가능)
library(svDialogs) # 사용을 위한 메모리에 로딩
svDialogs::dlg_input()

# input 값은 문자열로 저장됨
# 사용자가 문자 입력하지 않고 취소 시 character(0) 저장
user.input <- dlg_input('Input income')$res
is.numeric(user.input)  # FALSE
is.character(user.input) # TRUE
user.input

# 따라서 문자열을 숫자로 변환
income <- as.numeric(user.input)
income

# 세금 계산
tax <- income * 0.05
cat('세금: ', tax)
```



### 3. `print()` 와 `cat()`

* `print()`

  * 사용 특징
    * 하나의 값을 출력할 때
    * 데이터프레임과 같은 2차원 자료구조를 출력할 때
    * 출력 후 자동 줄바꿈 수행

* `cat()`

  * 사용 특징

    * 여러 개의 값을 연결해서 출력할 때

      (벡터는 출력 되지만, 2차원 자료구조는 출력안됨)

    * 출력 후 줄바꿈을 위해서는 '\n'이 필요

* 사용 예제

  ```R
  # print()
  > x <- 26
  > y <- '입니다'
  > z <- c(10, 20, 30, 40)
  > 
  > # 하나의 값 출력
  > print(x)
  [1] 26
  > print(y)
  [1] "입니다"
  > print(z)
  [1] 10 20 30 40
  
  # 데이터프레임 출력을 위한 iris 구조 확인
  > str(iris)
  'data.frame':	150 obs. of  5 variables:
   $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
   $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
   $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
   $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
   $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...
  # 데이터프레임 출력
  > print(iris[1:5,]) 
    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
  1          5.1         3.5          1.4         0.2  setosa
  2          4.9         3.0          1.4         0.2  setosa
  3          4.7         3.2          1.3         0.2  setosa
  4          4.6         3.1          1.5         0.2  setosa
  5          5.0         3.6          1.4         0.2  setosa
  > 
  > print(x, y) # 두개의 값 출력 에러 발생생
  Error in print.default(x, y) : invalid printing digits -2147483648
  추가정보: 경고메시지(들): 
  In print.default(x, y) : 강제형변환에 의해 생성된 NA 입니다
  
  # cat()
  > cat(x) # 하나의 값 출력
  26> cat(y) # 하나의 값 출력
  입니다> cat(z, '\n') # 두 값을 연결하여 출력
  10 20 30 40 
  > cat(x, y) # 두 값을 연결하여 출력
  26 입니다> cat(iris[1:5], '\n') # 데이터 프레임 출력(에러 발생)
  Error in cat(iris[1:5], "\n") : 타입 'list'인 인자 1는 'cat'에 의하여 다루어 질 수 없습니다
  ```






## - 파일을 이용해 데이터를 읽고 쓰기

###  1. 작업 폴더

* 작업 폴더

  * 자신이 읽거나 쓰고자 하는 파일이 위치하는 폴더

  * R에서 파일을 읽으려면 그 파일이 위치한 폴더의 경로와 함께 파일 이름을 지정해야함. 

    -> 작업 폴더를 미리 지정 시 파일 이름만으로도 데이터를 읽는 것이 가능

* 관련 예시

  ```R
  > # 작업 폴더 확인
  > getwd()
  [1] "D:/DataScience/RStudy
  
  > # 작업 폴더 변경
  > setwd('D:/DataScience')
  # 폴더 미존재시 에러 발생
  
  > # 파일 존재 여부 확인 : 작업 폴더 내 파일은 경로 설정을 할 필요가 없음
  > file.exists("test.data")
  [1] TRUE
  > 
  > # 파일이 없다면 FALSE 출력
  > file.exists('test.txt')
  [1] FALSE
  
  
  # 특정 폴더 내 파일 확인 : 파일명에 경로까지 모두 출력하고 싶다면 full.names = T
  dir()
  dir('D:/DataScience/RStudy')
  dir('D:/DataScience/RStudy', full.names = T)
  
  # 여러 개의 파일 리스트를 입력으로 받음 : 작업 폴더 내 파일의 정보 출력
  file.info("test.data")
  file.info(list.files())
  
  str(file.info(list.files()))
  
  # 작업 폴더 내 파일 정보 중 SIZE와 ISDIR 조회
  
  f_info <- file.info(list.files())
  class(f_info)
  f_info[, c('size', 'isdir')]
  ```



### 2. `.csv` 파일 읽기와 쓰기

* csv(comma separated values)는 콤마로 열과 열을 구분한 파일

* `read_csv()` 함수로 읽어오는 것이 가능

* `write.csv()` 함수로 저장이 가능

* 사용 예시

  ```R
  > # csv(comma separate value) 데이터 읽어오기
  > x <- read.csv("data/a.csv", stringsAsFactors = FALSE) # stringsAsFactors를 적용 시 string을 factor로 변환해 읽어옴
  경고메시지(들): 
  In read.table(file = file, header = header, sep = sep, quote = quote,  :
    'data/a.csv'에서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다
  
  > x # 읽은 데이터를 확인
    id     name score
  1  1   Mr Cho    80
  2  2  Mr Park    90
  3  3   Ms Kim    50
  > class(x)
  [1] "data.frame"
                
  > x[1, ] # 읽은 데이터에서 첫번째 행을 보여줌
    id    name score
  1  1  Mr Cho    80
                
  > str(x) # 읽은 데이터의 구조 확인
  'data.frame':	3 obs. of  3 variables:
   $ id   : int  1 2 3
   $ name : chr  " Mr Cho" " Mr Park" " Ms Kim"
   $ score: int  80 90 50
  > x$name <- as.character(x$name) # name을 chr형으로 변환
  
  > # 데이터를 csv 형으로 저장
  > write.csv(fruit, 'data/fruit.csv')
  Error in is.data.frame(x) : 객체 'fruit'를 찾을 수 없습니다
  
  > # fruit 객체를 지움
  > rm(fruit)
  경고메시지(들): 
  In rm(fruit) : 객체 'fruit'를 찾을 수 없습니다
  > ls()
  [1] "x"
  
  > # 저장한 fruit.csv를 불러오기
  > fruit <- read.csv('data/fruit.csv')
  > ls()
  [1] "fruit" "x" 
  ```

  

### 3. 엑셀 파일 읽기와 쓰기

* `xlsx` 패키지를 설치 후 사용해야 함.
* `read.xlsx()`함수를 이용해 읽어오기 가능

* 사용 예시

  ```R
  > install.packages('xlsx')
  > library(xlsx)
  
  > # xlsx 형으로 저장
  > write.xlsx(head(quakes), 'data/quakes.xlsx') 
  > 
  > # xlsx 파일 읽기
  > quakeXL <- read.xlsx('data/quakes.xlsx', 1)
  > quakeXL
    NA.    lat   long depth mag stations
  1   1 -20.42 181.62   562 4.8       41
  2   2 -20.62 181.03   650 4.2       15
  3   3 -26.00 184.10    42 5.4       43
  4   4 -17.97 181.66   626 4.1       19
  5   5 -20.42 181.96   649 4.0       11
  6   6 -19.68 184.31   195 4.0       12
  ```

  

## - 기타

### 실행 결과를 파일로 출력하기

* 중간에 발생하는 계산 결과나 작업 처리 결과를 화면이 아닌 파일로 출력해야 하는 경우

  * Ex. 처리 과정이 길고 시간이 오래 걸리는 작업을 저녁에 실행시키고, 다음날 아침에 결과를 확인하고 싶은 경우

  -> `sink()` 사용으로 해결 가능

* 방법

  1. `setwd()` 함수로 작업폴더 지정
  2. 파일 출력을 시작하는 곳과 끝내는 곳에 `sink()` 사용

* 사용 예시

  ```R
  > print('Begin work') # 화면으로 출력
  [1] "Begin work"
  > a <- 10; b <- 20
  > sink('result.txt', append=T) # 파일로 출력 시작
  > cat('a+b=', a+b, '\n') 
  > sink()        # 파일로 출력 정지
  > cat('hello world \n') # 화면으로 출력
  hello world 
  > sink('result.txt', append=T) # 파일로 출력 시작
  > cat('a*b=', a*b, '\n')
  > sink()    # 파일로 출력 정지
  > print('End work') # 화면으로 출력
  [1] "End work"
  ```

  * 중간의 `sink`로 묶여 있는 부분은 화면으로 출력되지 않음.

  