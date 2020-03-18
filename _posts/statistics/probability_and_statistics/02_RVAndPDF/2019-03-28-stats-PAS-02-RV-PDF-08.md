---
title: "결합 확률분포"
date: 2019-03-28
category:
  - Statistics
tag :
  - 이변량 결합 확률분포
  - 공분산
  - 상관계수
  - 독립성
  - 상관성
  - 포트폴리오 이론
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

# 8. 결합 확률분포

<br>

**학습 내용**

- 결합 확률
- 이변량 확률분포
- 공분산과 상관계수
- 독립성과 상관성
- 변수의 합

<br>

## 8.1 이변량 결합 확률분포

<br>

- 두 개의 확률변수 ($$X,\,Y$$)에 대한 확률
- 이변량 결합 확률분포

$$
\qquad
P(x,y) = P(X=x,\; Y=y)
$$

$$\qquad \Rightarrow \quad X = x \;$$ **AND** $$\; Y = y \;$$ 일 확률

<br>

- 이변량 결합 확률분포로 계산할 수 있는 수치들로는 **공분산**과 **상관계수**가 있다.

<br>

### 8.1.1 공분산 (covariance)

<br>

- 확률변수 X와 Y 사이의 공분산
- $$P(x_i,\,y_i)$$ : 결합 확률

$$
\qquad
\begin{align*}
Cov(X,Y) &= E[\left(X - \mu_x\right)\left(Y - \mu_y\right)] \\
\\
&= \sum_{all \; x_i} \, \sum_{all \; y_i} \; \left(x_i - \mu_x\right) \, \left(y_i - \mu_y\right) \, P(x_i, \, y_i)
\end{align*}
$$

<br>

- 공분산의 간편 수식

$$
\qquad
\begin{align*}
Cov(X,Y) &= E[X\,Y] - E[X]\,E[Y] \\
\\
&= \sum_{all \; x_i} \, \sum_{all \; y_i} \; x_i\,y_i\,P(x_i,\,y_i)\,-\, \mu_x\,\mu_y
\end{align*}
$$

<br>

- 분산과 공분산의 연결
- 확률변수 $$X$$의 분산은 확률변수 $$X$$ 끼리의 공분산과 같다.

$$
\qquad
Var(X) = Cov(X, X)
$$

<br>

### 8.1.2 상관계수 (correlation)

<br>

- 확률 변수 $$X$$와 $$Y$$ 사이의 상관계수
- 상관계수는 공분산과 비례한다.
- 공분산을 각각의 확률변수의 표준편차의 곱으로 나눠주면 상관계수가 된다.

$$
\qquad
Cor(X,Y) = {Cov(X,Y) \over \sigma_X\,\sigma_Y}
$$

<br>

- 상관계수는 -1 과 1 사이의 값을 갖는다.
- 공분산은 $$-\infty$$ 와 $$+\infty$$ 사이의 값을 갖지만 상관계수는 이 공분산을 표준편차로 나눠줬기 때문

$$
\qquad
-1 \leq Cor(X,Y) \leq 1
$$

<br>

- 상관계수는 선형관계의 **방향**과 **강도**를 나타낸다.

$$\qquad \rightarrow \quad Cor(X,Y) \; \gt \; 0$$ : $$X$$와 $$Y$$ 사이에 **양**의 선형관계가 있음

$$\qquad \rightarrow \quad Cor(X,Y) \; \lt \; 0$$ : $$X$$와 $$Y$$ 사이에 **음**의 선형관계가 있음

$$\qquad \rightarrow \quad Cor(X,Y) \; = \; 0$$ : $$X$$와 $$Y$$ 사이에 선형관계가 **없음**

<br>

## 8.2 독립성과 상관성

<br>

### 8.2.1 독립성

<br>

- 두 확률변수 $$X$$와 $$Y$$가 독립성을 가질 때, 두 확률변수의 결합 확률은 각각의 확률의 곱이다.

$$\qquad P(X,Y) = P(X) \, P(Y)$$

$$\qquad \Rightarrow \quad Cov(X,Y) = E[X \, Y] - E[X] \, E[Y] = E[X] \, E[Y] - E[X] \, E[Y] = 0$$

<br>

### 8.2.2 독립성 $$\; \rightarrow \;$$ 상관성

<br>

- 두 확률변수가 독립성을 가진다는 것은 "상관성 없음"을 내포한다.
- 독립성을 갖는 두 확률변수의 공분산이 0이므로, 상관계수 또한 0이 되기 때문

$$\qquad Cov(X,Y) = 0 $$

$$\qquad \rightarrow \quad Cor(X,Y) = {Cov(X,Y) \over \sigma_X\, \sigma_Y} = {0 \over \sigma_X\, \sigma_Y} = 0$$

$$\qquad \therefore \quad Cor(X,Y) = 0$$

<br>

### 8.2.3 상관성

<br>

- 상관계수는 -1 과 1 사이의 수치이다.
- **상관계수가 0**이라는 것은 두 확률변수 사이의 **상관성이 없다**는 것을 의미한다.

<br>

### 8.2.4 상관성 $$\; \nrightarrow \;$$ 독립성

<br>

- 두 확률변수 사이의 상관성이 없다고 해서 두 확률변수의 독립성을 내포하지 **않는다.**

<br>

### 8.2.5 독립성과 상관성의 예 (1)

<br>

- $$X$$ 와 $$Y$$ 동전 두 개를 동시에 던지는 경우를 가정
- 표본공간 : $$\{ HH, \, HT, \, TH, \, TT \}$$
- 두 동전 사이의 **독립성**을 확인

<br>

**Sol)**

**1) 개개 확률분포 함수 확인**

- $$P(X)$$
  - $$P(X \, = \, H) = {1 \over 2}$$
  - $$P(X \, = \, T) = {1 \over 2}$$
- $$P(Y)$$
  - $$P(Y \, = \, H) = {1 \over 2}$$
  - $$P(Y \, = \, T) = {1 \over 2}$$

<br>

**2) 독립성 확인**

- 표본 공간에서 선택

- $$P(X \, = \, H, \, Y \, = \, H) \, = \, {1 \over 4} \, = \, P(X \, = \, H) \times P(Y \, = \, H)$$
- $$P(X \, = \, H, \, Y \, = \, T) \, = \, {1 \over 4} \, = \, P(X \, = \, H) \times P(Y \, = \, T)$$
- $$P(X \, = \, T, \, Y \, = \, H) \, = \, {1 \over 4} \, = \, P(X \, = \, T) \times P(Y \, = \, H)$$
- $$P(X \, = \, T, \, Y \, = \, T) \, = \, {1 \over 4} \, = \, P(X \, = \, T) \times P(Y \, = \, T)$$

<br>

$$\qquad \therefore \quad $$ $$X$$ 와 $$Y$$ 는 서로 **독립 관계**이다.

<br>

### 8.2.6 독립성과 상관성의 예 (2)

<br>

- -1, 0, 1 에서 동일한 확률 1/3 을 갖는 확률변수 $$X$$ 와 $$Y = X^2$$ 로 정의되는 확률변수 $$Y$$ 가 있다.
- 두 확률변수의 결합확률은 다음과 같다.

$$
\qquad
P(X=-1, \, Y=1) = {1\over3}\;,\quad P(X=0, \, Y=0) = {1\over3} \;,\quad P(X=1, \, Y=1) = {1\over3}
$$

- 다음 물음에 답하여라.

<br>

**1) $$X$$ 와 $$Y$$ 가 서로 독립인 지 확인**

<br>

- $$X$$ 의 확률분포 함수
  - $$P(X = -1 ) = {1\over3}$$
  - $$P(X = 0 ) = {1\over3}$$
  - $$P(X = 1 ) = {1\over3}$$

<br>

- $$Y$$ 의 확률분포 함수
  - $$P(Y=0) = {1\over3}$$
  - $$P(Y=1) = {2\over3}$$

<br>

- 독립성 확인
  - $$P(X=-1, \, Y=1) = {1\over3} \quad \neq \quad P(X=-1) \; \times \; P(Y=1) = {1\over3} \times {2\over3} = {2\over9}$$
  - $$P(X=0, \, Y=0) = {1\over3} \quad \neq \quad P(X=0) \; \times \; P(Y=0) = {1\over3} \times {1\over3} = {1\over9}$$
  - $$P(X=1, \, Y=1) = {1\over3} \quad \neq \quad P(X=1) \; \times \; P(Y=1) = {1\over3} \times {2\over3} = {2\over9}$$

<br>

$$\qquad \therefore \quad P(X,Y) \neq P(X)\,P(Y)$$ 이므로 $$X$$ 와 $$Y$$ 는 서로 독립이 아닌 **종속 관계**이다.

<br>

**2) $$X$$ 와 $$Y$$ 사이의 상관계수 계산**

<br>
$$
\qquad
\begin{align*}
E[X] &= -1 \times P(X=-1) \; + \; 0 \times P(X=0) \; + \; 1 \times P(X=1) \\
\\
&= -{1\over3} \; + \; 0 \; + \; {1\over3} \\
\\
&= 0
\end{align*}
$$

$$
\qquad
\begin{align*}
E[Y] &= 0 \times P(Y=0) \; + \; 1 \times P(Y=1) \\
\\
&= 0 \; + \; 1 \times {2\over3} \\
\\
&= {2\over3}
\end{align*}
$$

$$
\qquad
\begin{align*}
E[X\;Y] &= E[X \; X^2] = E[X^3] \\
\\
&= -1 \times P(X=-1) \; + \; 0 \times P(X=0) \; + \; 1 \times P(X=1) \\
\\
&= -{1\over3} \; + \; 0 \; + \; {1\over3} \\
\\
&= 0
\end{align*}
$$

<br>
$$
\qquad
\therefore \quad Cov(X,Y) = E[X\;Y] - E[X]\;E[Y] = 0 - 0 \times {2\over3} = 0
$$
<br>

- 공분산이 0이므로 상관계수도 0이다.

$$
\qquad
\Rightarrow \quad Cov(X,Y) = 0 \quad \rightarrow \quad Cor(X,Y) = 0
$$

<br>

- 1) 에서 두 확률변수는 종속 관계(독립이 아님)임을 확인했는 데 두 확률변수의 상관계수가 0이다.

<br>

## 8.3 두 확률 변수의 합

<br>

### 8.3.1 이변량 확률 변수의 합

<br>

- 확률변수 $$X$$ 와 $$Y$$ 의 합의 경우를 생각해 보자.

<br>

**평균(기대값)**

$$
\qquad
E[X + Y] = E[X] + E[Y]
$$
<br>

**분산**

$$
\qquad
\begin{align*}
Var(X+Y) &= E\left[\left(X + Y - \mu_x - \mu_y\right)^2\right] \\
\\
&= E\left[\left( \left( X - \mu_x \right) - \left( Y - \mu_y \right) \right)^2\right] \\
\\
&= E\left[ \left(X-\mu_x\right)^2 + \left(Y-\mu_y\right)^2 + 2\left(X-\mu_x\right) \left(Y-\mu_y\right) \right] \\
\\
&= Var(X) + Var(Y) + 2\;Cov(X,Y) \\
\\
&= Var(X) + Var(Y) \quad \Leftarrow \quad X와\; Y가\,\; 서로\; 독립인\; 경우
\end{align*}
$$
<br>

### 8.3.2 다변량 확률 변수의 합

<br>

**평균(기대값)**

$$
\qquad
E[\;X_1 + X_2 + X_3 + \cdots \;] = E[X_1] \; + \; E[X_2] \; + \; E[X_3] \; + \; \cdots
$$
<br>

**분산**

$$\qquad Var(\;X_1 + X_2 + X_3 + \cdots \;) = Var(X_1) \;+\; Var(X_2) \;+\; Var(X_3) \;+\; \cdots $$

$$\quad\qquad\qquad\qquad\qquad\qquad\qquad\qquad \;+\; 2Cov(X_1,\,X_2) \;+\; 2Cov(X_1,\,X_3) \;+\; 2Cov(X_2,\,X_3) \;+\; \cdots$$

<br>

- 변수들이 서로 **독립적**이라면 공분산 항은 필요 없다.

$$
\qquad
Var(\;X_1 + X_2 + X_3 + \cdots \;) = Var(X_1) \;+\; Var(X_2) \;+\; Var(X_3) \;+\; \cdots
$$

<br>

## 8.4 현대 포트폴리오 이론 (MPT: Modern Portfolio Theory)

<br>

- 확률변수의 합을 현대 포트폴리오 이론에서 활용할 수 있다.

<br>

**포트폴리오(Portfolio)**

- Port (가지고 가다) + Folio (서류/증권) $$\quad \cong \quad$$ "서류철" or "서류가방"

<br>

### 8.4.1 포트폴리오 구성

<br>

**포트폴리오 구성 비율**

- $$N$$ 개의 자산으로 포트폴리오를 구성 (서브 인덱스 $$i = 1,\,2,\, \cdots\, N$$)
- 개개 자산이 포트폴리오에서 차지하는 비율 = $$w_i$$

$$\qquad \rightarrow \quad$$ $$w_i$$ 는 $$w_1 \;+\; w_2 \;+\; \cdots \;+\; w_N = 1$$ 제약 조건 충족

<br>

**포트폴리오 수익률**

- 확률변수 $$R_i$$ : 개개 자산의 **수익률**

$$\qquad \rightarrow \quad$$ 포트폴리오 수익률 $$R_P = w_1\,R_1 \;+\; w_1\,R_1 \;+\; \cdots w_N\,R_N$$

<br>

**리스크**

- 포트폴리오의 리스크는 수익률의 표준편차 $$\sigma_P$$ 또는 그것의 제곱인 분산 $$\sigma_P^2$$ 으로 나타낼 수 있다.
-  리스크 = 불확실성

<br>

**포트폴리오의 평균 수익률**

- 포트폴리오의 평균 수익률은 $$R_P$$ 의 기대값이다.
- *확률변수 합의 기대값 = 확률변수의 기대값의 합*

$$
\qquad
E[R_P] = w_1\,E[R_1] \;+\; w_2\,E[R_2] \;+\; \cdots \;+\; w_N\,E[R_N]
$$

<br>

**독립적인 자산들의 포트폴리오 리스크**

- 개개 자산이 서로 독립적인 경우 포트폴리오의 리스크는 다음과 같다.
- *포트폴리오의 분산 = 개별 종목의 분산의 합*

$$
\qquad
\sigma_P^2 \approx w_1^2\,\sigma_1^2 \;+\; w_2^2\,\sigma_2^2 \;+\; \cdots \;+\; w_N^2\,\sigma_N^2
$$

<br>

- 조건 1 : $$w_i = 1/N$$ (모든 자산이 같은 비율로 포트폴리오에 포함)
- 조건 2 : $$\sigma_1^2 \approx \sigma_2^2 \approx \cdots \approx  \sigma_N^2$$ (개별 자산의 리스크가 모두 동일)

$$
\qquad
\rightarrow \quad
\sigma_P^2 \approx N \, {1 \over N^2} \, \sigma^2 = {\sigma^2 \over N}
$$

<br>

- $$\sigma_P^2 = {\sigma^2 \over N}$$  는 $$N$$ 이 커지면 **0으로 수렴**한다.

<br>

$$\qquad \therefore \quad $$ 자산 여러 개를 묶어 포트폴리오로 만들면 **리스크 감소 효과**를 얻을 수 있다.
