# 연속확률분포

## 1. 연속확률변수(Continuous Random Variable)

* 어떤 범위에서 연속적인 값을 취할 수 있는 확률변수(실수)
* 전구의 수명, 몸무게, 체온 등등



### - 연속확률분포(Continuous Probability Distribution)

* 연속확률변수의 값에 대응하는 확률을 표시
* 일양균등분포, 정규분포, 표준정규분포, 지수분포

### - 3시그마 규칙

* **68-95-99.7 규칙** 또는 **경험적인 규칙(empirical rule)**이라고도 함.
* 평균에서 양쪽으로 3표준편차의 범위에 거의 모든 값들(99.7%)이 들어감
  * 약 68%의 값들이 평균에서 양쪽으로 1 표준편차 범위 $(\mu \pm \sigma)$에 존재한다.
  * 약 95%의 값들이 평균에서 양쪽으로 2 표준편차 범위$(\mu \pm 2\sigma)$에 존재한다.
  * 거의 모든 값들(실제로는 99.7%)이 평균에서 양쪽으로 3 표준편차 범위 $(\mu \pm 3\sigma)$에 존재한다.

[![3시그마 규칙](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Standard_deviation_diagram.svg/350px-Standard_deviation_diagram.svg.png)](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Standard_deviation_diagram.svg/350px-Standard_deviation_diagram.svg.png)

<center><small><a href='https://ko.wikipedia.org/wiki/68-95-99.7_%EA%B7%9C%EC%B9%99'>3시그마 규칙</a></small></center>





## 2. 연속확률분포

### 1) 정규분포(Normal Distribution)

* 가우시안 분포(Gaussian distribution)이라고도 함.
* 평균을 중심으로 좌우대칭이고 종모양을 갖는 확률분포
* 연속형 확률변수에 대한 분포
* 평균($\mu$)과 표준편차($\sigma$)로 모양이 결정된다.
  * 좌우 대칭, 종모양을 이룸
  * 중앙 한 점이 뾰족함
  * 평균 = 중앙값 = 최빈값
* 샘플을 추출해서 모집단의 모수를 예측할 때 이용한다.
* 통계분석 시 모집단의 분포를 정규분포라고 대부분 가정하고 통계분석을 함(중심극한정리)

* 정규분포의 확률 밀도 함수

  ![확률 밀도](https://wikimedia.org/api/rest_v1/media/math/render/svg/866e7df60005552a8abb63d9837dc91d987664f4)

  ​																													 $\mu$ : 평균 $\sigma$ : 표준오차

  [![정규분포의 확률밀도 함수](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Normal_Distribution_PDF.svg/1024px-Normal_Distribution_PDF.svg.png)](https://ko.wikipedia.org/wiki/%EC%A0%95%EA%B7%9C_%EB%B6%84%ED%8F%AC)

<center><small><a href='https://ko.wikipedia.org/wiki/%EC%A0%95%EA%B7%9C_%EB%B6%84%ED%8F%AC'>정규분포의 확률밀도 함수</a></small></center>



#### - 표준확률변수(stadardized random variable)

* 임의의 확률변수를 표준화시킴
* 측정단위 등과 관계없이 자료를 표준화 시킨 값
* 체리세프의 정리(Chebyshev's Theorem)
* 경험적 법칙(Empirical Rule)



#### - 표준 정규분포

* 정규 분포 밀도 함수에서 $Z=\frac{X - \mu}{\sigma}$를 통해 X를 Z로 정규화함으로써 평균이 0, 표준편차가 1인 표준정규분포를 얻을 수 있음.
* z-분포라고 부르고, z-분포로 하는 검정(test)을 z-검정(z-test)라고 한다. 



### 2) 연속균등분포(continuous uniform distribution)

* 분포가 특정 범위 내에서 균등하게 나타나 있을 경우

[![연속균등분포](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Uniform_distribution_PDF.png/270px-Uniform_distribution_PDF.png)](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Uniform_distribution_PDF.png/270px-Uniform_distribution_PDF.png)

<center><small><a href='https://ko.wikipedia.org/wiki/%EC%97%B0%EC%86%8D%EA%B7%A0%EB%93%B1%EB%B6%84%ED%8F%AC'>연속균등분포 확률 밀도 함수</a></small></center>



* $\mu = {a + b \over 2}$
* $\sigma =  \sqrt{(b-a)^2 \over 12}$
* $P(X = x) = {x-a \over b-a}$



### 3) 지수분포 (Exponential Distribution)

* 포아송 분포가 단위시간당 사건의 개수라면, 지수분포는 두 사건 사이의 시간에 대한 확률

[![지수분포](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Exponential_pdf.svg/270px-Exponential_pdf.svg.png)](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Exponential_pdf.svg/270px-Exponential_pdf.svg.png)

<center><small><a href='https://ko.wikipedia.org/wiki/%EC%A7%80%EC%88%98%EB%B6%84%ED%8F%AC'>연속균등분포 확률 밀도 함수</a></small></center>