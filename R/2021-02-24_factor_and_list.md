# factor(팩터)와 list(리스트)

* 팩터와 리스트는 벡터와 더불어 1차원 형태의 자료를 저장하는 자료구조
* 팩터는 주로 범주형 자료를 저장해 분석할 때 사용, 리스트는 여러 유형의 값들을 하나로 모아 저장할 필요가 있을 때 사용



## 1. 팩터

* 팩터

  * 문자형 데이터가 저장되는 벡터의 일종으로, 저장되는 문자값들이 **어떠한 종류를 나타내는 값(성별, 혈액형 등과 같은 범주형 자료)**일 때 사용.
  * 문자형 벡터를 만든 다음, `factor()`를 이용해 변환

  ```R
  > f <- c('A', 'B', 'B', 'O', 'AB', 'A') # 문자형 벡터 f 정의
  > f
  [1] "A"  "B"  "B"  "O"  "AB" "A" 
  
  > f.new <- factor(f) # 팩터 정의
  > f.new
  [1] A  B  B  O  AB A 
  Levels: A AB B O
  
  > f[5]
  [1] "AB"
  
  > f.new[5]
  [1] AB
  Levels: A AB B O
  
  > levels(f.new) # 팩터에 저장된 값의 종류 출력
  [1] "A"  "AB" "B"  "O" 
  
  > as.integer(f.new) # 팩터의 문자값을 숫자로 바꾸어 출력
  [1] 1 3 3 4 2 1
  
  > f.new[7] <- 'B' # 7번째에 'B' 저장
  > f.new[8] <- 'C' # 8번째에 'C' 저장
  경고메시지(들): 
  In `[<-.factor`(`*tmp*`, 8, value = "C") :
    invalid factor level, NA generated
  # 이미 지정된 값의 종류 외에 다른 값이 들어오는 것을 막는다.
  # 지정된 값 종류 이외의 값이 들어오면 경고메시지를 반환하고, 팩터 출력 시 <NA>로 변환함.
  > f.new
  [1] A    B    B    O    AB   A    B    <NA>
  Levels: A AB B O
  ```

  * `levels()` : 팩터에 저장된 값들의 종류를 알아내는 함수
  * `as.integer()` : 저장된 문자값을 숫자로 바꾸어 분석 작업에 활용 가능도록 만드는 함수



## 2. 리스트(list)

* 리스트는 **자료형이 다른 닶들을 한곳에 저장하고 다룰 수 있도록 해주는 수단**이다.

  * 여러 가지의 자료구조를 갖는 저장할 값을 저장하는 경우에 리스트가 유용
  * `list()` 를 사용해 리스트를 생성
  * 예시

  ```R
  > h.list <- c('bowling', 'tennis', 'ski') # 취미를 벡터에 저장
  > person <- list(name='Kim', age=25, student=TRUE, hobby=h.list) # 리스트 생성
  > person
  $name
  [1] "Kim"
  
  $age
  [1] 25
  
  $student
  [1] TRUE
  
  $hobby
  [1] "bowling" "tennis"  "ski"    
  
  > person[[1]] # 리스트의 첫번째 값 출력
  [1] "Kim
  
  > person$name # 리스트에서 값의 이름이 name인 값을 출력
  [1] "Kim"
  ```

  