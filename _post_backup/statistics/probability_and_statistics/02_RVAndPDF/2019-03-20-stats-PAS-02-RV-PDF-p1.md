---
title: "(실습) 이산확률"
date: 2019-03-20
category:
  - Statistics
tag :
  - 베르누이 확률분포
  - 이항 확률분포
  - 푸아송 확률분포
  - 누적확률
  - 분위수
  - 확률변수
sidebar:
  nav: sidebar-probabilityAndStatistics
mathjax: "true"
author_profile: false
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
header:
  overlay_image: /assets/images/dataScience.jpg
  overlay_filter: 0.5
comments: true
---
> 통계 > 확률과 통계 > 확률변수와 확률분포함수

<br>

# (실습) 이산 확률

<br>

**학습 내용**

- R 함수 이용 **베르누이 확률분포**의 **누적확률**, **분위수**, **랜덤넘버(확률변수)** 생성
- R 함수 이용 **이항 확률분포**의 **누적확률**, **분위수**, **랜덤넘버(확률변수)** 생성
- R 함수 이용 **푸아송 확률분포**의 **누적확률**, **분위수**, **랜덤넘버(확률변수)** 생성

<br>

## p1.1 R의 확률 관련 함수들

- R에는 여러 가지 확률과 관련된 함수들이 있다.

1. `dxxx()` : 확률 분포(distribution) 함수
2. `pxxx()` : 누적 확률 함수
3. `qxxx()` : 분위수(quartile) 함수
4. `rxxx()` : 랜덤 넘버 함수

- `xxx` : 확률분포의 명칭 (ex. 이항 확률분포 = `binom`, 푸아송 확률분포 = `pois`)

<br>

## p1.2 베르누이 확률분포

**베르누이 확률 분포 함수**  


$$
\qquad
P(x) = p^x \, \left(1-p\right)^{1-x}
$$
<br>

### p1.2.1 베르누이의 누적 확률

<br>

**`pbinom()`**

- 이항 확률 분포의 누적 확률을 계산하는 함수

- 베르누이 의 누적확률을 구하기 위해 사이즈를 1로 지정(`size=1`)

  ```R
  > args(pbinom)
  function (q, size, prob, lower.tail = TRUE, log.p = FALSE) NULL
  ```

  - `q` : 누적확률을 얻을 분위수 q 벡터
  - `size`  : 이항분포 $$B(n,\,p)$$의 $$n$$값 설정
  - `prob` : 이항분포 $$B(n,\,p)$$의 $$p$$ 값 설정

<br>

- $$p=0.5,\; x=0$$일 때, $$P(x = 0)$$의 누적 확률 계산

  ```R
  > pbinom(0,size=1,prob=0.5)
  [1] 0.5
  ```

<br>

- $$p=0.5,\; x=1$$일 때, $$P(x \leq 1)$$의 누적 확률 계산

  ```R
  > pbinom(1,size=1,prob=0.5)
  [1] 1
  ```

<br>

- $$p=0.3,\; x=0$$일 때, $$P(x = 0)$$의 누적 확률 계산

  ```R
  > pbinom(0,size=1,prob=0.3)
  [1] 0.7
  ```

<br>

- $$p=0.3,\; x=1$$일 때, $$P(x \leq 1)$$의 누적 확률 계산

  ```R
  > pbinom(1,size=1,prob=0.3)
  [1] 1
  ```

<br>

- $$p=0.7,\; x=0$$일 때, $$P(x = 0)$$의 누적 확률 계산

  ```R
  > pbinom(0,size=1,prob=0.7)
  [1] 0.3
  ```

<br>

- $$p=0.7,\; x=1$$일 때, $$P(x \leq 1)$$의 누적 확률 계산

  ```R
  > pbinom(1,size=1,prob=0.7)
  [1] 1
  ```

<br>

### p1.2.2 베르누이의 분위수

<br>

**`qbinom()`**

- 이항 확률분포의 백분위수를 구하는 함수
- `size=1`을 지정하여 베르누이 확률분포의 백분위수를 구하는 데 사용
- `pbinom()` 함수의 역의 값을 반환한다.

<br>

- 베르누이 확률 분포의 분위수를 계산하기 위해 `qbinom` 함수의 `size`를 1로 지정 (`size=1`)

  ```R
  > args(qbinom)
  function (p, size, prob, lower.tail = TRUE, log.p = FALSE)
  NULL
  ```

  - `p` : 분위수를 얻을 확률값의 벡터

<br>

- $$p=0.5$$일 때, $$P(x \leq X) = 0.1$$에 해당하는 $$X$$ 값(분위수) 계산

  ```R
  > qbinom(0.1,size=1,prob=0.5)
  [1] 0
  ```

<br>

- $$p=0.5$$일 때, $$P(x \leq X) = 0.9$$에 해당하는 $$X$$ 값(분위수) 계산

  ```R
  > qbinom(0.9,size=1,prob=0.5)
  [1] 1
  ```

<br>

### p1.2.3 베르누이의 랜덤넘버(확률변수) 생성

<br>

**`rbinom()`**

- 이항 확률변수를 랜덤하게 생성하는 함수

- `size=1`를 지정하여 베르누이 확률변수를 구하는 데 사용

  ```R
  > args(rbinom)
  function (n, size, prob)
  NULL
  ```

<br>

- 베르누이 확률분포(`size=1`)의 확률변수를 0.5의 확률(`prob=0.5`)로 20개(`n=20`) 생성

  ```R
  > rbinom(20,size=1,prob=0.5)
   [1] 0 0 1 1 0 0 0 0 0 0 0 1 0 1 0 1 1 0 0 1
  ```

  - $$p=0.5$$, 즉 1이 될 확률이 0.5이므로 0과 1이 절반씩 생성된다.

<br>

- 베르누이 확률분포(`size=1`)의 확률변수를 0.1의 확률(`prob=0.1`)로 20개(`n=20`) 생성

  ```R
  > rbinom(20,size=1,prob=0.1)
   [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 0
  ```

  - $$p=0.1$$, 즉 1이 될 확률이 0.1이므로 0이 훨씬 더 많이 생성된다.

<br>

- 베르누이 확률분포(`size=1`)의 확률변수를 0.9의 확률(`prob=0.9`)로 20개(`n=20`) 생성

  ```R
  > rbinom(20,size=1,prob=0.9)
   [1] 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
  ```

  - $$p=0.9$$, 즉 1이 될 확률이 0.9이므로 1이 훨씬 더 많이 생성된다.

<br>

## p1.3 이항 확률분포

**이항 확률분포 함수**  


$$
\qquad
P(x) = \binom{n}{x} p^x \, \left(1-p\right)^{n-x}
$$
<br>

### p1.3.1 이항 확률분포 함수 시각화

<br>

**`dbinom()` 함수**

- 이항 확률분포 함수를 생성하는 함수

  ```R
  > args(dbinom)
  function (x, size, prob, log = FALSE)
  NULL
  ```

<br>

**1) 0부터 20까지의 숫자 생성**

- `seq()` 함수를 이용하여 0부터 20까지의 숫자 생성

  ```R
  > x <- seq(0,20)
  > x
   [1]  0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
  ```

<br>

**2) $$n=20, \, p=0.5$$인 이항 확률분포 함수 그래프**

- `plot()` 함수 이용 그래프 생성

  ```R
  > plot(x, dbinom(x,size=20,prob=0.5), pch=19,col="blue")
  ```

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/r_img001.jpeg" width="600px">
</div>

- $$n=20$$이고, $$p=0.5$$이므로 **평균 10**($$n \times p = 10$$)을 중심으로 하는 그래프가 그려진다.

<br>

**3) $$n=20, \, p=0.7$$인 이항 확률분포 함수 그래프**

- `plot()` 함수 이용 그래프 생성

  ```R
  > plot(x, dbinom(x,size=20,prob=0.7), pch=19,col="red")
  ```

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/r_img002.jpeg" width="600px">
</div>

- $$n=20$$이고, $$p=0.7$$이므로 **평균 14**($$n \times p = 14$$)을 중심으로 하는 그래프가 그려진다.

<br>

**4) $$n=20, \, p=0.3$$인 이항 확률분포 함수 그래프**

- `plot()` 함수 이용 그래프 생성

  ```R
  > plot(x, dbinom(x,size=20,prob=0.3), pch=19,col="green")
  ```

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/r_img003.jpeg" width="600px">
</div>

- $$n=20$$이고, $$p=0.3$$이므로 **평균 6**($$n \times p = 6$$)을 중심으로 하는 그래프가 그려진다.

<br>

### p1.3.2 이항 확률분포의 누적확률

<br>

- `pbinom()` 함수를 이용하여 이항 확률분포의 누적확률 계산

<br>

- $$n=20, \, p=0.5$$ 일 때, $$P(x \leq 5)$$의 누적확률 계산

  ```R
  > pbinom(5,size=20,prob=0.5)
  [1] 0.02069473
  ```

<br>

- $$n=20, \, p=0.5$$ 일 때, $$P(x \leq 10)$$의 누적확률 계산

  ```R
  > pbinom(10,size=20,prob=0.5)
  [1] 0.5880985
  ```

<br>

- $$n=20, \, p=0.5$$ 일 때, $$P(x \leq 15)$$의 누적확률 계산

  ```R
  > pbinom(15,size=20,prob=0.5)
  [1] 0.994091
  ```

<br>

- $$n=20, \, p=0.5$$ 일 때, $$P(x \leq 20)$$의 누적확률 계산

  ```R
  > pbinom(20,size=20,prob=0.5)
  [1] 1
  ```

<br>

### p1.3.3 이항 확률분포의 분위수

<br>

- `qbinom()` 함수를 이용하여 이항 확률분포의 분위수 계산

<br>

- $$n=20, \, p=0.5$$ 일 때, $$P(x \leq X) = 0.5$$ 에 해당하는 $$X$$ 값(분위수) 계산

  ```R
  > qbinom(0.5,size=20,prob=0.5)
  [1] 10
  ```

<br>

- $$n=20, \, p=0.7$$ 일 때, $$P(x \leq X) = 0.5$$ 에 해당하는 $$X$$ 값(분위수) 계산

  ```R
  > qbinom(0.5,size=20,prob=0.7)
  [1] 14
  ```

<br>

### p1.3.4 이항 확률분포의 랜덤넘버(확률변수) 생성

<br>

- `rbinom()` 함수를 이용해 이항 확률변수 생성

<br>

- $$n=20, \, p=0.5$$인 10개의 이항 확률변수 생성

  ```R
  > rbinom(10,size=20,prob=0.5)
   [1] 11 12  9  9 11  7  9 12  7 14
  ```

<br>

- $$n=20, \, p=0.3$$인 10개의 이항 확률변수 생성

  ```R
  > rbinom(10,size=20,prob=0.3)
   [1] 3 4 5 4 7 5 4 6 8 7
  ```

<br>

## p1.4 푸아송 확률분포

**푸아송 확률분포 함수**  


$$
\qquad
P(x) = {\lambda^x \, e^{-\lambda} \over x!}
$$
<br>

### p1.4.1 푸아송 확률분포 함수 시각화

<br>

**`dpois()` 함수**

- 푸아송 확률분포 함수를 생성하는 함수

  ```R
  > args(dpois)
  function (x, lambda, log = FALSE)
  NULL
  ```

<br>

**1) 0부터 20까지의 숫자 생성**

- `seq()` 함수를 이용하여 0부터 20까지의 숫자 생성

  ```R
  > x <- seq(0,20)
  > x
   [1]  0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
  ```

<br>

**2) $$\lambda=1$$인 푸아송 확률분포 함수 그래프**

- `plot()` 함수 이용 그래프 생성

  ```R
  > plot(x, dpois(x,lambda=1), pch=19,col="blue")
  ```

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/r_img004.jpeg" width="600px">
</div>

- $$\lambda=1$$이므로, 평균이 1인 그래프가 그려짐

<br>

**3) $$\lambda=2$$인 푸아송 확률분포 함수 그래프**

- `plot()` 함수 이용 그래프 생성

  ```R
  > plot(x, dpois(x,lambda=2), pch=19,col="red")
  ```

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/r_img005.jpeg" width="600px">
</div>

- $$\lambda=2$$이므로, 평균이 2인 그래프가 그려짐

<br>

**4) $$\lambda=4$$인 푸아송 확률분포 함수 그래프**

- `plot()` 함수 이용 그래프 생성

  ```R
  > plot(x, dpois(x,lambda=4), pch=19,col="green")
  ```

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/r_img006.jpeg" width="600px">
</div>

- $$\lambda=4$$이므로, 평균이 4인 그래프가 그려짐

<br>

**5) $$\lambda=8$$인 푸아송 확률분포 함수 그래프**

- `plot()` 함수 이용 그래프 생성

  ```R
  > plot(x, dpois(x,lambda=8), pch=19,col="magenta")
  ```

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/r_img007.jpeg" width="600px">
</div>

- $$\lambda=8$$이므로, 평균이 8인 그래프가 그려짐

<br>

### p1.4.2 푸아송 확률분포의 누적확률

<br>

- `ppois()` 함수를 이용하여 푸아송 확률분포의 누적확률 계산

<br>

- $$\lambda = 3$$일 때, $$P(x \leq 1)$$의 누적확률 계산

  ```R
  > ppois(1,lambda=3)
  [1] 0.1991483
  ```

<br>

- $$\lambda = 3$$일 때, $$P(x \leq 3)$$의 누적확률 계산

  ```R
  > ppois(3,lambda=3)
  [1] 0.6472319
  ```

<br>

- $$\lambda = 3$$일 때, $$P(x \leq 4)$$의 누적확률 계산

  ```R
  > ppois(4,lambda=3)
  [1] 0.8152632
  ```

<br>

### p1.4.3 푸아송 확률분포의 분위수

<br>

- `qpois()` 함수를 이용하여 푸아송 확률분포의 분위수 계산

<br>

- $$\lambda = 2$$ 일 때, $$P(x \leq X) = 0.5$$ 에 해당하는 $$X$$ 값(분위수) 계산

  ```R
  > qpois(0.5,lambda=2)
  [1] 2
  ```

<br>

- $$\lambda = 4$$ 일 때, $$P(x \leq X) = 0.5$$ 에 해당하는 $$X$$ 값(분위수) 계산

  ```R
  > qpois(0.5,lambda=4)
  [1] 4
  ```

<br>

- $$\lambda = 8$$ 일 때, $$P(x \leq X) = 0.5$$ 에 해당하는 $$X$$ 값(분위수) 계산

  ```R
  > qpois(0.5,lambda=8)
  [1] 8
  ```

<br>

### p1.4.4 푸아송 확률분포의 랜덤넘버(확률변수) 생성

<br>

- `rpois()` 함수를 이용해 푸아송 확률변수 생성

<br>

- $$\lambda = 2$$인 20개의 푸아송 확률변수 생성

  ```R
  > rpois(20,lambda=2)
   [1] 3 1 2 1 3 3 3 1 2 1 1 1 0 2 1 4 2 3 3 1
  ```

<br>

- $$\lambda = 4$$인 20개의 푸아송 확률변수 생성

  ```R
  > rpois(20,lambda=4)
   [1]  5 10  3  5  7  5  4  5  3  2  3  8  5  9  2  2  1  4  2  1
  ```

<br>

- $$\lambda = 8$$인 20개의 푸아송 확률변수 생성

  ```R
  > rpois(20,lambda=8)
   [1]  5  8 10  6  4  7  5  8  7  6  8  7  3  6 14  9  7  4  7  3
  ```

<br>
