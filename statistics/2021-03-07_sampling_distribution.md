# 표본분포와 추정

## 1. 통계적 추론

* 통계적 추론(statistical inference)

  * 모집단에서 추출한 표본을 이용하여 모집단의 특성(모수)를 예측하는 과정
  * 추정과 가설검정을 포함한다.
  * 모수(parameter) : 모집단의 특성을 나타내는 수치(Ex. 평균, 비율, 분산 등)
    * 모집단이 정규분포 $N(\mu, \sigma^2)$을 따를 때, 모수는 $\mu$와 $\sigma^2$
  * 통계량(statistics) : 표본에서 구한 특성값

  

* 표본조사

  * 관심대상은 매우 광범위하고 다양하지만 **그 중에서 일부만 추출**하여 그 자료를 분석함으로써 우리의 관심대상 전체에 대한 결론을 도출함
  * 문제점 : 표본에 따라 표본추출변동이 발생(모집단의 일부인 표본만을 이용해 추측하므로 **불확실성**을 내포하고 있음)

[![표본조사](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F995927505BE5B4872C)](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F995927505BE5B4872C)

<center><small><a href='https://twoearth.tistory.com/26'>표본조사</a></small></center>



* 표본추출방법
  - 단순임의 추출법
    - 모집단의 모든 원소가 표본으로 뽑힐 가능성이 같도록 표본을 추출하는 방법
    - 랜덤 표본(random sample)
      - 단순임의 추출법에 의해서 추출된 표본
      - 복원 추출 / 비복원 추출



* 표본분포(sampling distribution)

  * 모집단에서 추출한 표본크기 $n$개인 추정치(estimator)의 확률분포
  * 모집단에서 일정한 크기($n$)으로 표본을 모두($k$개) 뽑아서 각 표본의 평균을 계산했을 때, 그 표본의 평균의 확률 분포
  * 모집단 분포의 모양과 상관없이 표본분포는 정규분포 모양

* 표본분포의 특징

  * 평균 : 모집단의 평균과 표본들의 평균은 같음

    $E(\bar{X}) = \mu$

  * 표본오차(sampling error) : 통계량과 모수 간의 오차

    $error = \bar{x} - \mu$

  * 표준오차(standard error of the mean) : 오차의 범위는 표준오차로 결정

    $\sigma_\bar{x} = {\sigma \over \sqrt{n}}$

    * 표본의 개수가 늘어날수록 오차범위는 줄어든다.

  

  ### - 중심극한 정리(Central limit theorem)

  * 만약, 평균이 $\mu$이고 표준편차가 $\sigma$인 모집단으로부터 추출된 표본의 개수가 $n$개라면, 표본의 분포는 평균이 $\mu$이고 표준편차가 ${\sigma \over \sqrt{n}}$인 정규분포를 따른다.
  * 모집단 전체를 조사하지 않고도 표본평균을 통해 모집단의 특성을 확률적으로 추론해 낼 수 있는 근거를 제시하기 때문에 통계학에서 가장 중요한 이론 중 하나

  

## 2. 통계적 추론의 구분

* 통계(statistics)란

  * 관심대상에 대해 관련된 자료(data)를 수집하고 -> **표본추출(sampling)**
  * 요약하고 -> **기술통계학(descriptive statistics)**
  * 불확실한 사실에 대한 결론이나 일반적인 규칙성을 추리하는 학문 -> **추리통계학(inferential statistics)**

* 통계적 추론(statstical inference)

  * 모집단에서 추출한 표본을 이용해 모집단에 관한 추측이나 결론을 이끌어내는 과정

  

#### 1) 추정

- 표본의 평균과 표준오차(Standard Error of Means)를 구해서 모수의 범위를 구하는 것

- 신뢰구간 : 일정한 확률 범위 내에서 모수의 값이 포함될 가능성이 있는 범위

- 종류

  - 점 추정(point estimation)

    - 모수를 하나의 값으로 추정하는 것

    - 점 추정으로 얻은 추정량의 특징

      - 추출된 표본에 따라 달라짐
      - 추정하는 모수와 일치한다고 보장할 수 없다.

      

  - 구간 추정(interval estimation)

    - 모수를 포함하리라고 예상되는 구간을 제시하여 모수를 측정하는 것
    - 신뢰구간(confidence interval) : 일정한 신뢰수준 하에서의 모수가 포함될 구간
    - 신뢰수준(confidence level) : 특정 구간 안에 모수가 포함될 확률
    - 같은 신뢰수준에서는 길이가 짧은 신뢰구간이 더 좋다.

  -> 우리는 표본으로부터 값을 구했기 때문에 표본오차가 존재한다 -> 추정 시에는 점추정보다는 구간추정을 이용함

  * 추정량으로 하나의 값만 제시하는 것은 의미가 없다. -> 추정치가 모수와 일치하지 않기 때문에, 그 정확도를 나타내는 표준오차와 함께 제시해야 의미가 있다.

  

##### - 신뢰구간(Confidence Interval)

* 일반적으로 신뢰수준은 $(1-\alpha)$로 측정 ($\alpha$ : 오차)

* 신뢰수준의 확률 : 90%, 95%, 99% 중에서 95%

* 신뢰구간 95%의 의미

  * 동일한 모집단에 대해서 동일한 방법으로 표본을 다시 뽑아서 신뢰구간을 구하게 되면, 100번중 95번은 모수를 포함한다.(표본분포의 의미)
  * 표본을 여러 번 추출하여 같은 방법으로 신뢰구간을 구할 때, 이 구간 중에서 모평균(모수)를 포함하는 구간의 비율이 95%에 가깝다.
  * 추정된 구간 L과 U가 모집단 평균을 포함하게 될 것이라는 믿음의 정도가 95%가 된다는 것

  

* 방법
  * 모집단의 표준편차 $\sigma$를 알 경우 : **표준정규분포**
  * 모집단의 표준편차 $\sigma$를 모를 경우 : **Student t-분포**

* t-분포(Student t Distribution)

  * 정규분포나 표준정규분포 : 모집단의 분산을 알고 있을 경우에 사용

  * 실제로 우리는 모집단의 분산을 모르고, 표본을 통해서 가설을 검정하므로 t-분포 이용

  * 자유도(degree of freedom: $n-1$)에 의해서 모양이 결정

  * 표본의 크기가 증가($n\geq30$)하면 분포는 정규분포에 접근

  * 특징 

    * 정규분포처럼 종모양의 대칭분포

    

[![신뢰구간 추정](https://lh3.googleusercontent.com/proxy/UvezbRF3FhLYpPgILgJgr0BwPDOzh5KPmdG6Kf1qMulf7GG_FG_-uRW-plaCVsDnPme7Rr9Jjmhpo4rocA)](https://lh3.googleusercontent.com/proxy/UvezbRF3FhLYpPgILgJgr0BwPDOzh5KPmdG6Kf1qMulf7GG_FG_-uRW-plaCVsDnPme7Rr9Jjmhpo4rocA)

<center><small><a href='http://jangun.com/study/IntroductionStatistics.html'>신뢰구간 추정</a></small></center>

##### - 표본 크기의 결정

* 자료를 수집하기 전에 원하는 정확도로 모집단에 대한 추정을 하기 위해 필요한 표본의 크기를 정하는 법

  Ex. 신뢰구간에서 표본의 크기 $n$이 커질수록 신뢰구간이 짧아진다.



#### 2) 가설검정(Hypothesis test)

* 모수는 얼마이다라고 정하고, 그것이 맞는지 틀리는지를 검증하는 방법

- 표본분포를 이용해 모집단의 특성에 대한 가설의 진위를 가리는 것
  - 모수에 대한 두 가지 가설 중에서 어느 것이 옳은지 판단하는 것
- 유의수준 : 모수와 통계량의 차이가 커서 확률적으로 가설을 기각할 수 있는 값



### - 좋은 추정량의 선택 기준

#### 1) 불편성(unbiasedness)

* 편의(biased)가 없다는 뜻
  * 편의 : 추정량의 기대치와 모수와의 차이
* 불편추정량(unbiased estimator)
  * 추정량의 기대값이 모수와 같은 추정량
  * 불편성을 만족

[![불편추정량](https://lh3.googleusercontent.com/proxy/BTcAC4L94z4fscZ7TP4Bb6YxNW6AD8rUGJrRQJg91rNtGTn8L0B7CdN5cPEt_1n0BFXQgC1IADoPb0vMe24)](https://lh3.googleusercontent.com/proxy/BTcAC4L94z4fscZ7TP4Bb6YxNW6AD8rUGJrRQJg91rNtGTn8L0B7CdN5cPEt_1n0BFXQgC1IADoPb0vMe24)

<center><small><a href='http://jangun.com/study/StatisticsConceptProblem.html'>불편추정량</a></small></center>



#### 2) 효율성(efficency)

* 불편추정량 중에서 분산이 작은 추정량이 갖는 성질
* 추정량이 불편성을 만족한다고 하더라도, **분산이 크다면 편의가 있는 추정량보다 더 낫다고 할 수 없음**

[![효율성](http://www.ktword.co.kr/img_data/458_2.jpg)](http://www.ktword.co.kr/img_data/458_2.jpg)

<center><small><a href='http://www.ktword.co.kr/test/view/view.php?m_temp1=458&id=1240'>효율성</a></small></center>



#### 3) 일치성(consistency)

* 표본의 크기가 증가할수록 추정량이 모수에 일치하는 경우
* 표본 크기가 커질수록 추정량이 모수에 점근적(asymptotic)으로 근접하는 성질



#### 4) 충분성(sufficiency)

* 어떤 추정량이 모수 $\theta$에 대해 가장 많은 정보를 제공하는가 여부를 나타내는 성질



