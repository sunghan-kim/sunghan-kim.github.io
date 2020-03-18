---
title: "연속확률 Ⅱ"
date: 2019-03-26
category:
  - Statistics
tag :
  - 정규분포
  - 표준화
  - 표준정규분포
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

# 5. 연속 확률변수와 확률밀도함수의 유형 - 2

<br>

**학습 내용**

- 정규분포함수
- 정규 확률변수의 합
- 누적확률
- 표준화와 표준정규분포함수

<br>

## 5.1 정규분포함수 (Normal)

<br>

- 정규분포함수는 구간 $$(-\infty, \, +\infty)$$에 대해서 정의되어 있음

$$
\qquad
f(x) = {1 \over \sigma \sqrt{2\pi} } \, e^{ -{ {(x-\mu)^2} \over 2 \sigma^2} }
$$

<br>

- 평균 = $$\mu$$
- 분산 = $$\sigma^2$$
- 표준편차 = $$\sigma$$

<br>

- "확률변수 $$X$$가 정규확률분포를 따른다."

$$
\qquad
 \Leftrightarrow \quad X \sim N(\mu, \sigma^2)
$$

<br>

### 5.1.1 평균 ($$\mu$$) 의 역할

<br>

- $$\mu$$는 확률분포함수의 **봉우리의 위치**를 나타낸다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img021.jpg" width="500px">
</div>

<br>

### 5.1.2 표준편차 ($$\sigma$$) 의 역할

<br>

- $$\sigma$$가 커질수록 확률분포함수의 **폭**이 더 넓어진다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img022.jpg" width="500px">
</div>

<br>

## 5.2 정규 확률변수의 합

<br>

- 확률변수 $$X$$와 $$Y$$가 서로 **독립**이며 정규확률분포를 따를 때,

$$
\qquad
X \sim N(\mu_1, \, \sigma_1^2)
$$

$$
\qquad
Y \sim N(\mu_2, \, \sigma_2^2)
$$

<br>

- 두 확률변수의 합($$X + Y$$)은 또 다른 정규 확률변수이다.
  - 평균은 두 정규 확률변수의 합
  - 분산 또한 두 정규 확률변수의 합

  $$
  \qquad
  X \, + \, Y \sim N(\mu_1 + \mu_2, \, \sigma_1^2 + \sigma_2^2)
  $$

<br>

- 두 확률변수의 차($$X-Y$$)는 또 다른 정규 확률변수이다.

  - 평균은 두 정규 확률변수의 차
  - **분산**은 두 정규 확률변수의 **합**이다. (분산은 계속해서 증가한다.)

  $$
  \qquad
  X \, - \, Y \sim N(\mu_1 - \mu_2, \, \sigma_1^2 + \sigma_2^2)
  $$

<br>

## 5.3 정규분포의 누적확률 (Cumulative Distribution Function, CDF)

<br>

- 정규분포의 누적확률 $$CDF(x)$$ 은 구간 $$( - \infty, \, x]$$ 에서 아래의 면적과 같다.

<br>

$$
\qquad
\begin{align*}
CDF(x) &= P( - \infty \lt X \leq x) \\
\\
&= \int_{-\infty}^{x} \, f(y) \, dy
\end{align*}
$$



<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img023.jpg" width="400px">
</div>

<br>

- $$CDF(x)$$는 **$$x$$가 증가**하면 **1로 수렴**한다.

<br>

- ex) $$\mu = 0$$인 정규 확률분포 함수의 $$CDF(x)$$
  - $$x \rightarrow - \infty$$ 일 때, $$CDF(x)$$는 0으로 수렴
  - $$x \rightarrow + \infty$$ 일 때, $$CDF(x)$$는 1으로 수렴
  - $$x = 0$$ 일 때, $$CDF(x) = 0.5$$ 이다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img024.jpg" width="400px">
</div>

<br>

### 5.3.1 구간의 확률

<br>

- $$P(x_1 \leq X \leq x_2)$$ 와 같은 구간의 확률은 $$CDF(x)$$로 구할 수 있다.

$$
\qquad
P(x_1 \leq X \leq x_2) = CDF(x_2) \, - \, CDF(x_1)
$$

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img025.jpg" width="600px">
</div>

<br>

## 5.4 표준 정규분포 함수 (Standard Normal)

<br>

- 표준 정규분포 함수는 구간 $$(-\infty, \, +\infty)$$에 대해서 정의되어 있음

$$
\qquad
f(x) = {1 \over \sqrt{2\pi} } \, e^{ -{ x^2 \over 2 } }
$$

<br>

- 평균 = 0
- 분산 = 1
- 표준편차 = 1

<br>

- "확률변수 $$X$$가 표준 정규확률분포를 따른다."

$$
\qquad
 \Leftrightarrow \quad X \sim N(0, 1)
$$

<br>

## 5.5 표준화

<br>

- 확률변수 $$X$$가 정규분포를 따른다. $$\quad \rightarrow \quad X \sim N(\mu, \sigma^2)$$
- 이 확률변수 $$X$$를 다음의 방식으로 표준 정규 확률변수 $$Z$$로 변환할 수 있다.
- 이 확률변수 $$Z$$는 표준 정규분포를 따른다. $$\quad \rightarrow \quad Z \sim N(0, 1)$$
- 정규분포를 따르는 확률변수를 표준 정규분포를 따르는 확률변수로 변환하는 것을 **표준화**라고 한다.

$$
\qquad
Z = {X - \mu \over \sigma}
$$

<br>

- 표준화된 $$X$$의 값 $$z$$를 *z-score*, 즉 **"표준점수"**라고 부른다.

$$
\qquad
z-score = {x - \mu \over \sigma}
$$

<br>

- 반대로, 표준 정규 확률변수 $$Z$$를 정규분포 $$N(\mu, \sigma^2)$$를 따르는 확률변수로 변환할 수도 있다.

$$
\qquad
X = \sigma \, Z + \mu
$$

<br>

## 5.6 표준 정규분포의 분위수 (Quantile of Standard Normal)

<br>

- 분위수 또는 백분위수는 **신뢰구간 계산**에 필요함
- 분위수를 $$z_{\alpha}$$ 라고 표기
- $$z_\alpha$$는 우측 꼬리의 면적이 $$\alpha$$와 같은 변수값을 의미 ($$z_\alpha$$ 보다 더 클 확률이 $$\alpha$$ 이다.)

$$
\qquad
P(z_\alpha \lt Z) = \alpha
$$

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img026.jpg" width="300px">
</div>

<br>

### 5.6.1 $$\alpha = 0.05$$

<br>

- $$z_{0.05} \cong 1.645$$
  - 1.645 이상이 될 확률은 0.05 이다.

<br>

- $$- z_{0.05} \cong -1.645$$
  - 정규분포 함수는 좌우 대칭이다.
  - -1.645 이하가 될 확률은 0.05 이다.

<br>

- 양쪽 꼬리에서 0.05의 확률씩을 떼어내면 중간 부분의 확률은 0.90 이 된다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img027.jpg" width="300px">
</div>

<br>

### 5.6.2 $$\alpha = 0.025$$

<br>

- $$z_{0.025} \cong 1.96$$
  - 1.96 이상이 될 확률은 0.025 이다.

<br>

- $$- z_{0.025} \cong -1.96$$
  - -1.96 이하가 될 확률은 0.025 이다.

<br>

- 양쪽 꼬리에서 0.025의 확률씩 떼어내면 중간 부분의 확률은 0.95 가 된다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img028.jpg" width="300px">
</div>

<br>

## 5.7 문제

<br>

- A군이 시험문제를 푸는 데 문항 당 평균 50초가 걸리고 표준편차는 20초이다.
- 48초와 54초 사이에 문항을 풀 확률은 얼마인가?
- 다음과 같은 표준 정규분포의 CDF(누적확률) 표를 활용하여 계산

|  z   | CDF(z) |
| :--: | :----: |
| -0.2 | 0.4207 |
| -0.1 | 0.4602 |
|  0   |  0.5   |
| 0.1  | 0.5398 |
| 0.2  | 0.5793 |

<br>

**Answer)**

- 1) $$x_1 = 48$$ 와 $$x_2 = 54$$ 를 표준화

$$
\qquad
z_1 = {x_1 - \mu \over \sigma} = {48 - 50 \over 20} = -{2 \over 20} = -0.1
$$

$$
\qquad
z_2 = {x_2 - \mu \over \sigma} = {54 - 50 \over 20} = {4 \over 20} = 0.2
$$

<br>

- 2) CDF 표 활용, 구간의 확률 계산

$$
\qquad
\begin{align*}
P(z_1 \leq Z \leq z_2) &= CDF(z_2) - CDF(z_1) = CDF(0.2) - CDF(-0.1) \\
\\
&= 0.5793 \; - \; 0.4602 = 0.1191
\end{align*}
$$
