---
title: "연속확률 Ⅲ"
date: 2019-03-26
category:
  - Statistics
tag :
  - 지수확률분포
  - 카이제곱분포
  - 자유도
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

# 6. 연속 확률변수와 확률밀도함수의 유형 - 3

<br>

**학습 내용**

- 지수 확률분포함수
- 카이제곱 확률분포함수
- 카이제곱 확률변수의 합

<br>

## 6.1 지수 확률분포함수 (Exponential)

<br>

- 푸아송 사건 사이의 거리(시간)을 확률로 모델링하는 함수

$$
\qquad
f(x) = \lambda e^{-\lambda x}
$$

<br>

- $$x$$는 **양수**이어야 한다. ($$x \geq 0$$)
- $$\lambda$$는 유일한 파라미터이고 양의 수치이어야 한다.
- 보통 $${1 \over \lambda}$$는 시간의 의미를 갖는다.

<br>

- "확률변수 $$X$$가 지수 확률분포를 따른다."

$$
\qquad
\Leftrightarrow \quad X \sim Exp(\lambda)
$$

<br>

### 6.1.1 지수 확률분포함수의 평균, 분산, 표준편차, 누적확률

<br>

- 평균 = $${1 \over \lambda}$$
- 분산 = $${1 \over \lambda^2}$$
- 표준편차 = $${1 \over \lambda}$$ (평균과 표준편차가 같음)
- 지수분포의 누적확률 : $$CDF(x) = 1 - e^{-\lambda x}$$

<br>

### 6.1.2 $$\lambda$$의 역할

<br>

- $$\lambda$$는 $$x = 0$$ 일 때의 지수 확률분포함수의 값이다.
- $${1 \over \lambda}$$ 는 지수 확률분포함수의 평균이다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img029.jpg" width="400px">
</div>

<br>

- $$\lambda=1, \quad \lambda=2, \quad \lambda=3$$ 일 때의 각각의 지수 확률분포함수는 아래의 그림과 같다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img030.jpg" width="400px">
</div>

<br>

### 6.1.3 지수분포의 누적확률함수 (Cumulative Density Function, CDF)

<br>

- $$CDF(x)$$는 $$x$$가 증가하면 1로 수렴한다.

<br>

- ex) $$\lambda = 2$$ 일 때의 지수 확률분포함수($$f(x)$$)와 누적 확률 함수($$CDF(x)$$)

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img031.jpg" width="400px">
</div>

<br>

### 6.1.4 지수 확률분포함수 문제

<br>

- 자동차가 20개월 마다 한 번씩 고장난다는 전제로 지수 확률분포로 모델링하여 고장 주기가 15개월과 20개월 사이일 확률을 구하여라.

<br>

**Answer)**

- 1) $$\lambda$$ 계산

$$
\qquad
\lambda = {1 \over 20} = 0.05
$$

<br>

- 2) CDF를 활용해 구간의 확률 계산

$$
\qquad
\begin{align*}
P(15 \leq X \leq 20) &= CDF(20) - CDF(15) = (1 - e^{-0.05 \times 20}) - (1 - e^{-0.05 \times 15}) \\
\\
&= 0.6321 - 0.5276 = 0.1045
\end{align*}
$$

<br>

## 6.2 카이제곱 분포함수 (Chi Square)

<br>

- $$k$$개의 표준정규분포를 따르는 **독립적인** 확률변수 $$X_i \sim N(0,1)$$가 있을 때, 카이제곱 확률변수 $$Q$$는 이 확률변수들의 제곱의 합이다.

$$
\qquad
Q = X_1^2 + X_2^2 + \cdots + X_i^2
$$

<br>

- $$k$$ : 자유도 (degree of freedom)

<br>

- "확률변수 $$Q$$가 카이제곱 확률분포를 따른다."

$$
\qquad
\Leftrightarrow \quad Q \sim \chi^2(k)
$$

<br>

- 카이제곱 확률분포함수는 구간 $$\left(0, \, +\infty \right)$$ 에 대해서 정의되어 있다.

$$
\qquad
f(x) = {1 \over 2^{k \over 2} \; \Gamma({k \over 2})} \; x^{ {k \over 2}-1} \; e^{-{x \over 2}}
$$

<br>

### 6.2.1 카이제곱 분포함수의 평균, 분산, 표준편차

<br>

- 평균 = $$k$$
- 분산 = $$2k$$
- 표준편차 = $$\sqrt{2k}$$

<br>

### 6.2.2 자유도($$k$$)의 역할

<br>

- $$k=1, \quad k=2, \quad k=3$$ 일 때의 각각의 카이제곱 확률분포함수는 아래의 그림과 같다.
- $$k$$ 가 커질수록 확률의 무게가 오른쪽으로 이동한다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img032.jpg" width="400px">
</div>

<br>

### 6.2.3 카이제곱 확률변수의 합

<br>

- 확률변수 $$Q_1$$와 $$Q_2$$가 서로 독립적이며 다음과 같이 카이제곱 확률분포를 따를 때,
  - $$Q_1 \sim \chi^2(k_1)$$ : $$Q_1$$은 자유도가 $$k_1$$인 카이제곱 확률변수
  - $$Q_2 \sim \chi^2(k_2)$$ : $$Q_2$$은 자유도가 $$k_2$$인 카이제곱 확률변수

<br>

- 두 카이제곱 확률변수의 합은 각각의 자유도의 합을 자유도로 같은 또 다른 카이제곱 확률변수이다.

$$
\qquad
Q_1 + Q_2 \sim \chi^2(k_1+k_2)
$$

<br>

**증명**

$$\qquad Q_1 + Q_2 = \{X^2 + X^2 + \cdots + X^2\} + \{X^2 + X^2 + \cdots + X^2\}$$

$$\qquad\qquad\qquad\qquad\qquad\quad k_1개 \qquad\qquad\qquad\qquad k_2개$$

<br>

$$\qquad \therefore \quad Q_1 + Q_2 \sim \chi^2(k_1 + k_2)$$
