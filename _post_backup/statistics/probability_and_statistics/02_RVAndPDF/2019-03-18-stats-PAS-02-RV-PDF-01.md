---
title: "이산확률 Ⅰ"
date: 2019-03-18
category:
  - Statistics
tag :
  - 확률변수
  - 확률분포함수
  - 모집단
  - 모수
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

# 1. 이산 확률변수와 확률분포함수의 유형

<br>

**학습 내용**

- 확률변수와 확률분포함수
- 모집단과 모수
- 기대값 (모평균)의 법칙
- 모분산의 법칙

<br>

## 1.1 확률변수 (random variable)

- 확률변수 : 확률실험의 각 결과에 실수를 부여하는 **함수**
- 확률변수의 값은 하나의 수치로 나타낸 사건이다.
- ex) 동전을 던지는 실험
  - 앞면(H) $$\rightarrow$$ 1
  - 뒷면(T) $$\rightarrow$$ 0

<br>

## 1.2 확률변수의 유형

<br>

### 1.2.1 이산확률변수 (discrete random variable)

- 셀 수 있는 가지수의 값을 가지는 확률변수
- ex) 주사위를 던져서 나오는 눈의 수 : $$\{1, 2, 3, 4, 5, 6\}$$

<br>

### 1.2.2 연속확률변수 (continuous random variable)

- 셀 수 없는 (무한대) 가지수의 값을 가지는 확률변수
- ex) 1년 연봉, 성인 남성의 신장 등

<br>

## 1.3 확률분포함수 (probability distribution function)

<br>

### 1.3.1 이산확률분포함수

- 이산확률변수가 가지는 값가 이것의 **확률** 사이의 **대응 관계**
- **확률변수** : 영문 **대문자**로 표기 (ex. 확률변수 $$X$$)
- **확률변수의 값** : 영문 **소문자**로 표기 (ex. 확률변수의 값 $$x$$)
- 확률변수 $$X$$의 값이 $$x$$일 확률 : $$P(X = x)$$ 또는 $$P(x)$$ 로 표기

<br>

## 1.4 확률밀도함수 (probability density function)

<br>

### 1.4.1 연속확률분포함수 / 확률밀도함수

- 확률밀도함수를 사용하여 연속확률변수의 값이 **특정 구간에 속할 확률**을 나타냄

<br>

## 1.5 이산 확률의 필수 조건

- 다음 조건이 충족되어야 함
- $$0 \leq P(x) \leq 1$$
- $$\sum_{all\, x_i}P(x_i) = 1$$

<br>

## 1.6 모집단과 모수

<br>

### 1.6.1 모집단 (population)

- 분석 대상 전체를 의미
- 실존 또는 개념적 존재

<br>

### 1.6.2 모수 (parameter)

- 모집단의 특성을 나타냄
- ex) 모평균, 모분산, 모표준편차 등

- 모집단의 특성을 묘사하기 위해 확률분포함수를 사용할 수 있음
- ex) 모평균을 확률분포함수를 사용하여 계산

<br>

## 1.7 이산확률을 따르는 모집단의 평균 (모평균)

<br>

### 1.7.1 모평균

- 확률변수 $$X$$의 **기대값(expected value)**
- $$E[X]$$ 로 나타냄

- 이산확률변수가 가질 수 있는 값들에 확률을 **가중치**로 곱해서 평균을 구한 것($$\cong$$ 더한 것)

$$
\qquad
\mu = E[X] = \sum_{all\,x} x P(x)
$$

- 모평균은 보통 $$\mu$$로 표기

<br>

### 1.7.2 기대값(모평균)의 법칙

- $$E[c] = c \quad \Leftarrow \quad c : 상수$$
- $$E[X \; + \; Y] = E[X] + E[Y]$$
- $$E[c \; X] = c \; E[X]$$
- $$E[X \; + \; c] = E[x] + c$$

<br>

## 1.8 이산확률을 따르는 모집단의 분산 (모분산)

<br>

### 1.8.1 모분산

- 확률변수 $$X$$의 모분산
- $$Var(X)$$ 와 같이 나타냄
- 모평균을 기준으로한 **편차의 제곱**에 확률을 **가중치**로 곱해서 평균을 구한 것($$\cong$$ 더한 것)

$$
\qquad
\sigma^2 = Var(X) = \sum_{all\,x} \left(x - \mu \right)^2 \, P(x)
$$

- 모분산은 보통 $$\sigma^2$$로 표기

<br>

### 1.8.2 모분산 간편 수식

- 모분산 = 확률변수의 제곱의 기대값 - 기대값의 제곱

$$
\qquad
\sigma^2 = \left(\sum_{all\,x} x^2 \; P(X)\right) - \mu^2 = E[X^2] - \left(E[X]\right)^2
$$

<br>

### 1.8.3 모표준편차

- 모분산의 제곱근을 계산

$$
\qquad
\sigma = \sqrt{\sigma^2}
$$

<br>

### 1.8.4 모분산의 법칙

- $$Var(c) =  0 \quad \Leftarrow \quad 상수의\, 분산은 \,0$$
- $$Var(X + c) = Var(X)$$
- $$Var(c \, X) = c^2 \, Var(X) \quad \Leftarrow \quad 상수(c)가 \, 제곱되는 \, 것 \, 주의$$
- $$Var(X + Y) = Var(X) + Var(Y) + 2 Cov(X,Y)$$
- $$Var(X + Y) = Var(X) = Var(Y) \quad \Leftarrow \quad X와\, Y가\, 독립인 \, 경우에만! $$

<br>

## 1.9 모평균과 모분산 문제

<br>

### 1.9.1 문제 (1)

- 동전 던지기 게임
- 앞면이 나오면 $$X = 100$$을 받고, 뒷면이 나오면 $$0$$을 받음
- 게임의 참가비용은 40
- 수익의 평균과 표준편차는?

**Answer)**

- 수익을 나타내는 확률변수 = $$X - 40$$
- 수익의 **모평균**:

$$
\qquad
\begin{align*}
E[X-40] &= E[X] - 40 \\
\\
&= 100 \times P(X = 100) + 0 \times P(X = 0) - 40 \\
\\
&= 100 \times {1 \over 2} - 40 \\
\\
&= 50 - 40 \\
\\
&= 10
\end{align*}
$$

- 수익의 **모분산**:

$$
\qquad
\begin{align*}
Var(X - 40) &= Var(X) = E[X^2] - \left(E[X]\right)^2 \\
\\
&= 100^2 \times P(X = 100) + 0^2 \times P(X = 0) - 50^2 \quad \Leftarrow \quad E[X]= 50\\
\\
&= 10000 \times {1 \over 2} - 2500 = 5000 - 2500 = 2500
\end{align*}
$$

- 수익의 **표준편차** (리스크):

$$
\qquad
\sqrt{2500} = 50
$$
