---
title: "연속확률 Ⅰ"
date: 2019-03-22
category:
  - Statistics
tag :
  - 연속 확률변수
  - 연속 확률분포 함수
  - 확률밀도함수
  - 연속 균등분포
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

# 4. 연속 확률변수와 확률밀도함수의 유형 - 1

<br>

**학습 내용**

- 연속 확률변수와 연속 확률밀도함수
- 연속 균등분포 함수

<br>

## 4.1 연속 확률변수 (continuous random variable)

<br>

- **셀 수 없는 (무한대)** 가지 수의 값을 가지는 확률변수
- ex) 1년 연봉, 성인남성의 신장 등

<br>

- 연속 확률변수의 경우 확률은 **구간**에 대해서 정의되어 있다.
  - 즉, $$P(X = x_0)$$와 같이 특정 위치에 대한 확률은 의미가 없다.
  - **$$P(x_1 \leq X \leq x_2)$$**와 같이 $$X$$가 어느 구간에 있을 확률이 의미가 있다.

<br>

## 4.2 연속 확률밀도 함수 (probability density function)

<br>

- 연속 확률분포 함수 = 확률밀도함수
- 이산 확률분포 함수와는 다르게 이것 자체만으로는 **확률의 의미가 없다.**
- 이것을 **사용**하여 연속 확률변수의 값이 특정 **구간에 속할 확률**을 나타낼 수 있다.
- **연속 확률분포 함수** 또는 **확률밀도함수**를 $$f(x)$$와 같이 표기
  (구간의 확률 $$P(x)$$와는 구분)

<br>

### 4.2.1 확률밀도함수에서 확률의 의미

<br>

- 어느 **특정 위치**($$x_0$$)에 대한 확률밀도함수의 값($$f(x_0)$$)은 확률의 **의미가 없다.**

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img015.jpg" width="500px">
</div>

<br>

- $$P(x_1 \leq X \leq x_2)$$와 같이 $$X$$가 **어느 구간**에 있을 확률이 **의미가 있다.**

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img016.jpg" width="500px">
</div>

<br>

### 4.2.2 확률밀도함수의 조건

<br>

- 확률밀도함수는 아래의 2가지 조건을 만족해야 한다.

<br>

1) $$0 \leq f(x)$$

- 상한이 없다. (1 이상이 되어도 상관 없다.)  

<br>

2) $$f(x)$$가 정의되어 있는 구간에서 $$f(x)$$ 아래의 총 면적은 1과 같아야 한다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img017.jpg" width="700px">
</div>

<br>

## 4.3 연속 균등분포 (Uniform distribution)

<br>

- 연속 균등확률분포함수는 구간 $$[a, \, b]$$에 대해서 정의되어 있다.

$$
\qquad
f(x) = {1 \over (b - a)}
$$

$$\qquad \rightarrow \quad$$ 이외의 구간에서는 $$f(x) = 0$$이다.

<br>

- 확률밀도가 균등하므로(즉, 확률밀도는 상수) 확률은 구간 $$[x_1, \, x_2]$$의 폭($$x_2 - x_1$$)에 비례한다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img018.jpg" width="500px">
</div>

<br>

- "확률변수 $$X$$가 연속 균등확률분포를 따른다."

$$
\qquad
 \Leftrightarrow \quad X \sim Unif(a, b)
$$

<br>

### 4.3.1 연속 균등분포의 평균, 분산, 표준편차

<br>

1) **평균**

<br>
$$
\qquad
E[X] = \int_{a}^{b} {x \over (b-a)} \, dx = {1 \over 2} \, (a + b)
$$

<br><br>

2) **분산**

<br>
$$
\qquad
\begin{align*}
E[X^2] - \left(E[X]\right)^2 &= \int_{a}^{b} {x^2 \over (b-a)} \, dx \; - \; \left[{1 \over 2} \, (a + b)\right]^2 \\
\\
&= {a^2 + ab + b^2 \over 3} \;-\; {a^2 + 2ab + b^2 \over 4} \\
\\
&= {1 \over 12} \, (b-a)^2
\end{align*}
$$

<br><br>

3) **표준편차**

<br>
$$
\qquad
\sqrt{ {1 \over 12} \, (b-a)^2 } \; = \; {1 \over \sqrt{12}} \, (b-a)
$$
<br><br>

### 4.3.2 연속 균등분포의 누적확률 (Cumulative Distribution Funcion, CDF)

<br>

**연속균등분포의 누적확률 $$CDF(x)$$**


- 구간 $$(-\infty,\,x]$$에서 $$f(x)$$ 아래의 면적

<br>

$$
\qquad
\begin{align*}
CDF(x) &= P(-\infty \lt X \leq x) \\
\\
&= \int_{-\infty}^{x}\,f(y)\,dy
\end{align*}
$$

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img019.jpg" width="400px">
</div>

<br>

- $$CDF(x)$$는 **$$x$$가 증가**하면 **1로 수렴**한다.

<br>

- ex) $$a=-1, \, b=+1$$

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img020.jpg" width="400px">
</div>

<br>

### 4.3.3 연속 균등분포 문제

<br>

- 백열전구의 수명 $$X$$는 연속균등분포를 따르며 5000시간에서 7000시간 사이이다.
- 다음 물음에 답하여라.

<br>

**1) 백열전구가 사용시간 6000시간과 7000시간 사이에서 타버릴 확률은?**

- 연속균등분포의 확률밀도 함수 : $$f(x) = {1 \over (7000 - 5000)} = 0.0005$$

<br>

$$
\qquad
\begin{align*}
P(6000 \leq X \leq 7000) &= (7000 - 6000) \times f(x) \\
\\
&= 1000 \times 0.0005 \\
\\
&= 0.5
\end{align*}
$$
<br><br>

**2) 백열전구의 수명이 5500시간 이하일 확률은?**

$$
\qquad
\begin{align*}
P(x \leq 5500) &= P(5000 \leq x \leq 5500) \\
\\
&= (5500 - 5000) \times f(x) \\
\\
&= 500 \times 0.0005 \\
\\
&= 0.25
\end{align*}
$$
<br><br>

**3) 백열전구의 수명이 최소 사용시간 5500시간 이상일 확률은?**


$$
\qquad
\begin{align*}
P(x \geq 5500) &= P(5500 \leq x \leq 7000) \\
\\
&= (7000 - 5500) \times f(x) \\
\\
&= 1500 \times 0.0005 \\
\\
&= 0.75
\end{align*}
$$
<br><br>

**4) 백열전구의 수명이 정확하게 6000시간일 확률은?**


$$
\qquad
\begin{align*}
P(X = 6000) &= P(6000 \leq x \leq 6000) \\
\\
&= (6000 - 6000) \times f(x) \\
\\
&= 0 \times 0.0005 \\
\\
&= 0
\end{align*}
$$
<br>
