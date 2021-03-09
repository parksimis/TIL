# 가설검정

* 표본분포를 이용하여 모집단 특성에 대한 가설의 진위를 가리는 것



## 1. 가설(Hypothesis)

* 가설의 유형

  * $H_0$ : 귀무가설 (Null Hypothesis)

    * 기존에 알려져 있는 사실(status quo)
    * 주장하려는 가설과 반대되는 가설

  * $H_1$ : 대립가설 또는 연구가설 (Alternative Hypothesis)

    * 새로운 사실, 현재 믿음에 변화가 있는 사실, 뚜렷한 증거로 입증하려고 하는 주장
    * 주장하려는 가설

    

* **통계적 가설검정에서는 귀무가설을 받아들일 것인지, 아니면 기각(reject)할 것인지를 검증**

  * 귀무가설을 기각하면 연구가설을 받아들이는 것.

* 가설 $H_0$가 사실이라는 가정 하에 검정이 이루어지므로 가설검정의 초점은 $H_0$에 있다. 

  * $H_0$은 현재 알려진 사실이므로 명확히 가설로 진술할 수 있기 때문이다. 이러한 사실을 바탕으로 표본을 구해서 이를 검증할 수 있다.



* 귀무가설의 증명
  * 귀무가설은 증명할 수 있는가? (100% -> 95%(신뢰구간) - 5%(유의수준))

[![가설검정의 오류](https://lh3.googleusercontent.com/proxy/HtauS2DSR5IAHs-wGm-gtVKIqjd0HA9msNXP1-J9f01NhA501eHhX811Zn_S-EDlw5QQBBsQCekJ7qupetna8UKDpjzMPUQpsxtzkNRCpVkGhcJ3UHavFaLIwejD6Zl3somWlWO0jEVM8S4ZNFzXIdnnodptr458e4hejcGQGzHQJWjOyhP-dd2Eoacn8YWLtRqZuku6LxBrhap5KlQRWPlCe6asLSFKuPH3JFXnY6BU5mhpcpEJ0-ILif5aAsECP9COWnMtVHhI6u7TLDaVdu8p4MpKjjVoCQ4getbg_U8kTV9LlUeiPkzxntve0KNv3x3adfK4pSdNc5PO7RrLC0UrjGdzlVdWKmVuSY9wzw)](https://m.blog.naver.com/PostView.nhn?blogId=mykepzzang&logNo=220885492245&proxyReferer=https:%2F%2Fwww.google.com%2F)

<center><small><a href='https://m.blog.naver.com/PostView.nhn?blogId=mykepzzang&logNo=220885492245&proxyReferer=https:%2F%2Fwww.google.com%2F'>가설검정의 오류</a></small></center>



* 가설검정에서 발생할 수 있는 오류
  * 1종 오류는 위험하기 때문에 최대 허용치를 정해 놓음(유의수준)
  * 1종 오류를 제한하면서, 검정력($1-\beta$)를 최대화하는 것이 목표이다.

[![가설검정에서 발생할 수 있는 오류](https://lh3.googleusercontent.com/proxy/ha96Bh-osOcc1ZWr73EwDUMq2L867EBrGnoPyeGtO3e7MY355bhSqhVgYRYSKr-RWPSfxuhlET3OkiQRU-mneW2OelS0GlXoEuhacfUxoWsafJRKIuNU55WZJySMIHDghvP5VCTaav2WIAHKRZDr-fZ-GQxRfVXtGppL1CxFM994_nlaM7EvxSO3i8WWUxUVcaXbZhCHZxxqDIigMJHagvcCAT-8uEfeZR__9zEKkuXlUPWXeQGvgfuL8wHNyTsUY7N9HZ3hT-RcPav7cSAnAuKShJmQW04XX14tqfUBMYMa1HIKZjXoZ5rXalRTusoFmDJ489D_tREr_hlMSgu9NmYuUBSs8JuNwiumO9wUmEq8)](https://lh3.googleusercontent.com/proxy/ha96Bh-osOcc1ZWr73EwDUMq2L867EBrGnoPyeGtO3e7MY355bhSqhVgYRYSKr-RWPSfxuhlET3OkiQRU-mneW2OelS0GlXoEuhacfUxoWsafJRKIuNU55WZJySMIHDghvP5VCTaav2WIAHKRZDr-fZ-GQxRfVXtGppL1CxFM994_nlaM7EvxSO3i8WWUxUVcaXbZhCHZxxqDIigMJHagvcCAT-8uEfeZR__9zEKkuXlUPWXeQGvgfuL8wHNyTsUY7N9HZ3hT-RcPav7cSAnAuKShJmQW04XX14tqfUBMYMa1HIKZjXoZ5rXalRTusoFmDJ489D_tREr_hlMSgu9NmYuUBSs8JuNwiumO9wUmEq8)

<center><small><a href='https://blog.naver.com/mykepzzang/220885492245'>가설검정에서 발생할 수 있는 오류</a></small></center>

* 두 가지 오류($\alpha, \beta$)의 크기를 줄여야 하겠지만,
  * 제 1종의 오류를 작게하면 제 2종의 오류가 커지고,
  * 제 2종의 오류를 작게하면, 제 1종의 오류는 커지게 된다. (trade-off)
* 오류의 원인은 표본오차(또는 추정오차)에 있음



#### - 유의수준($\alpha$)

* $\alpha$를 이용한 검증 : $H_0$가 진실임을 증명
* $H_0$이 진실인데 $H_0$를 기각할 수 있는 오류를 범할 확률의 최대 허용치
* 0.01, 0.05, 0.1 중에서 0.05(5%)



#### - 검정력(Power)

* $\beta$를 이용한 검증 : $H_0$가 거짓임을 증명
* $H_0$가 거짓일 때, $H_0$을 기각할 수 있는 확률 : $(1-\beta)$
* 80 ~ 95%



#### - 가설검정

$\alpha$는 현재사실을 근거로 검증하기 때문에, $\beta$를 통한 검증보다는 $\alpha$를 이용한 가설검정을 실시





## 2. 통계적 가설검정(Statistical Hypothesis Test)

* 통계적 가설 : 통계 검정을 위해서 사용하는 가설
* 통계검정 : 모집단의 모수 $(\mu_0, \pi_0, \sigma_0)$를 추측
* **가설 검정은 $H_0$가 진실인지를 검증함.** (=)
  * One Sample t-test 일 때 , $H_0 : \mu = \mu_0$
  * Independent Sample t-test일 때 , $H_0 : \mu_1 = \mu_2$
  * Paired Sample t-tes일 때, $H_0 : \mu_d = 0$
  * Correlation Analysis일 때, $H_0 : \rho = 0$



#### 1) 통계적 가설검정의 절차

* 가설 설정
  * 귀무가설($H_0$), 연구가설($H_1$)
  * 우측검정(right-sided test), 좌측검정(left-sided test), 양측검정(two-sided test)
* 유의 수준($\alpha$) 및 임계치(critical value) 결정
  * 주로 0.05(5%)
  * 임계치 : 귀무가설을 기각하거나 채택할 수 있는 기중($z$ 또는 $t$)
* 검정통계량 (test statistics), 유의확률($p$ - value) 계산
* 임계치와 통계량 검정 및 결론 도출



##### - 단측검정과 양측검정

* 단측검정(One-sided Test)

  * **대립가설**의 내용이 "크다" 또는 "작다" 등 **한쪽 방향**으로만 서술되는 경우의 가설검정
  * 단측검정의 대립가설이 채택되려면, 대립가설에 서술된 방향의 증거가 필요함.

  1) 우측 검정

  * B 햄버거 1개의 칼로리는 500kcal 이하이다.
    * $H_0 : \mu \le 500$ 
    * $H_1 : \mu > 500$

  2) 좌측 검정

  * 새롭게 개발한 진통제의 지속시간은 5시간 이상이다.
    * $H_0 : \mu \ge 5$ 
    * $H_1 : \mu < 500$

* 양측검정(Two-sided Test)
  * **대립가설**의 내용이 "같지 않다" 또는 "차이가 있다" 등 **양쪽 방향**으로 서술되는 경우의 가설검정
  * 귀무가설을 기각할 수 있는 **기각역은 양쪽방향**으로 주어짐
  * B 아이스크림의 파인트 용량은 320g이다.
    * $H_0 : \mu = 5$ 
    * $H_1 : \mu \neq 500$

[![단측검정과 양측검정](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fvz99i%2Fbtqxf5hHyzE%2Fgpiual95FF4nyFC9MK9GD0%2Fimg.png)](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fvz99i%2Fbtqxf5hHyzE%2Fgpiual95FF4nyFC9MK9GD0%2Fimg.png)

<center><small><a href='https://dbrang.tistory.com/1407'>단측검정과 양측검정</a></small></center>



##### - p값과 유의수준

* 유의수준
  * 가설을 검정하기 전에 설정된 유의수준
* $p-$value
  * 검정과정에서 밝혀진(계산된) 유의수준
  * 귀무가설이 맞는다는 가정 하에서 표본 통계량의 값이 나타날 확률



* 검정 과정에서 계산된 p-값(확률)이 유의수준 $\alpha$보다 작다($p-$값 $< \alpha$)는 것
  * 잘못된 결론(귀무가설이 실제로 맞음에도 귀무가설을 기각)을 내릴 확률(오류)이 극히 작다는 것
  * 우리가 내릴 결론은 오류에 의한 것으로 볼 수 없으며, **귀무가설($H_0$)이 사실이 아님을 의미**함(귀무가설을 기각)

* $p-$값(확률)이 유의수준보다 크다($p-$값 $> \alpha$)는 것
  * 잘못된 결론(귀무가설이 실제로 맞음에도 귀무가설을 기각)을 내릴 확률(오류)이 크다는 것
  * **귀무가설($H_0$)이 사실임을 의미** (귀무가설을 기각하지 않음)