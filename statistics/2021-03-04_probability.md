# 확률

* 확률

  어떤 사건(event)이 일어날 가능성

  * 동전을 던졌을 때 앞면이 나올 가능성
  * 주사위를 던졌을 때 특정 눈금이 나올 확률

## 1. 확률의 개념

##### 1) 경험적 확률(상대도수 확률)

* 동일한 조건 하에서 같은 **실험을 반복**했을 때 어떤 특정한 사건이 발생한 비율, 즉 **상대도수**로 계산
* 실험을 통한 확률(실험의 반복 횟수는 충분히 커야 한다.)
* Ex. K 공장의 생산품 중에서 불량품이 나올 확률



##### 2) 고전적 확률(논리적 확률)

* 이론적 확률
  * Ex. 주사위를 던졌을 때 1이 나올 확률 (1/6)

* **어떤 한 시행에서 나타날 수 있는 결과의 개수(n)**가 정해져 있음
* 각각의 결과가 나타날 가능성이 모두 동일할 것이라는 논리적 추론에 근거를 둔다.
* 현실 세계에서 단일사상이 발생할 가능성이 동일하지 않는 경우도 존재한다.
  * Ex. 특정한 치료법에 의해 질병이 치료될 확률을 구하는 경우

* 무한한 근원사상으로 이루어진 표본공간 존재
  * Ex. 한 공정에서 불량품이 생산될 확률을 구하는 경우

[![확률의 종류](https://blog.kakaocdn.net/dn/Tl9Xn/btqy0RCoSmU/S2khprcFEfhz1kyM3ewul0/img.png)](https://blog.kakaocdn.net/dn/Tl9Xn/btqy0RCoSmU/S2khprcFEfhz1kyM3ewul0/img.png)

<center><small><a href='https://jinnnii.tistory.com/7'>확률의 종류</a></small></center>

##### 3) 주관적 확률

* 새로운 상품이 시장에서 성공할 확률(주로 전문가의 의견)
* 논리적 확률, 경험적 확률 : 계산된 확률을 근간으로 의사결정이 가능
* 특정사건이 발생할 가능성은 **개인적인 지식과 경험 또는 가치관에 따라 달라**질 수 있는 확률
  * 야구에서 주자가 2루에 있을 때 감독은 어떤 대타를 기용할 것인가?
  * 상황에 따라 어떤 투수로 교체할 것인가는 경험적 확률만으로 결정한다고 볼 수 있다.





### - 공리적 해석

* 모든 확률을 다음의 공리(Axiom)를 만족
  1. 반드시 일어나는 사건이 확률은 1이다.
  2. 모든 확률은 0 ~ 1 의 값을 갖는다.
  3. 서로 독립적인 사건 A와 B에 대해 두 사건이 나타날 확률은 각 사건이 나타나는 확률의 합과 같다.

### - 용어

* 실험(random experiment)
  * 사전에 알려지지 않은 결과를 관찰하는 과정
* 표본 공간(sample space)
  * 어떤 실험이나 관측에서 발생 가능한 모든 결과의 집합
  * $\Omega$ 또는 $S$로 표기
  * Ex. 손님이 물건을 구매할까 안할까? $S$ = {'구매', '비구매'}
* 표본점(sample point)
  * 한번의 실험 또는 관측으로부터 얻을 수 있는 결과(근원 사상)
  * $\omega$ 로 표기
* 사건 또는 사상(event)
  * 하나 또는 둘 이상의 단일 사상의 집합 : 사건
  * 표본공간에서 결과의 부분집합
  * 일어날 수 있는 모든 가능한 결과 중에서 특정한 결과의 모임
    * Ex. A = {구매}
    * 연속형일수도 있음.
      * 표본공간 S = {m:m > 0}
      * 주문 금액이 50,000에서 100,000일 사건 A = {m:50,000 < m < 100,000}

### - 순열(Permutation)

* 서로 다른 n개 중 r개를 선택해 순서를 고려해 나열하는 방법의 수

  * Ex. 6곡이 노래가 들어있는 기기에서 6곡을 순서대로 듣고자 할 때 중복 없이 들을 수 있는 경우의 수는?
    $$
    6 \times 5 \times 4 \times 3 \times 2 \times 1 = 720
    $$

    $$
    \mathrm{n} \times (\mathrm{n} - 1) \times (\mathrm{n} - 2) \times \cdots \times = \mathrm{n}!
    $$

    

### - 조합(Combination)

* n개의 사물 중 r개를 순서를 고려하지 않고 뽑는 방법의 수

  * Ex. 6곡의 노래가 들어있는 기기에서 6곡을 순서에 상관없이 3곡을 들을 수 있는 경우의 수(중복 없음)
    $$
    _\mathrm{n}C_\mathrm{k} = \frac{_\mathrm{n}P_\mathrm{k}}{\mathrm{k}!}=\frac{\mathrm{n}!}{\mathrm{k}!(\mathrm{n}-\mathrm{k})!}
    $$
    





## 2. 확률 규칙

#### 1) 여사건

* 표본 공간 중에서 $\Alpha$ 사건이 발생하지 않을 확률
* $A^\acute{}$가 사건 $\Alpha$의 여사건이라고 할 때, $P(A^\acute{}) = 1 - P(A)$



#### 2) 교사건(Intersection of Events)

* A and B



#### 3) 합사건(Union of Events)

* A or B



#### 4) 조건부 확률

* A라는 조건이 주어진 상태에서 B가 발생할 확률

  어떤 사상 $\Alpha$가 주어져 있을 때 사상 $\Beta$가 일어날 조건부 확률은

   $P(B|A)$로 표시하며, $P(A) > 0$라면, 
  $$
  P(B|A) = {P(A \cap B) \over P(A)}
  $$
  

  

## 3. 베이즈 정리(Bayes' Rules)

* 사전(prior, uncoditional) 확률 과 사후(posterior, conditional) 확률 사이의 관계를 조건부확률을 이용해서 계산

  상호배반 사상 $B_1, B_2, \cdots , B_n $이 표본공간 $S$의 분할이며, 모든 $i$에 대하여 $P(B_i) > 0$이라 하면, 

  $P(A)>0$인 사상 $A$에 대해 다음이 성립

  [![베이즈 정리](https://raw.githubusercontent.com/angeloyeo/angeloyeo.github.io/master/pics/2020-01-09-Bayes_rule/pic1.png)](https://raw.githubusercontent.com/angeloyeo/angeloyeo.github.io/master/pics/2020-01-09-Bayes_rule/pic1.png)

  <center><small><a href='https://angeloyeo.github.io/2020/01/09/Bayes_rule.html'>베이즈 정리</a></small></center>

* 새로운 근거가 제시될 때, 사후 확률의 변화와 관계
* 또는 $P(B|A)$ 를 알 경우 $P(A|B)$를 계산