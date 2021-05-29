---
title: "연속확률 Ⅳ"
date: 2019-03-26
category:
  - Statistics
tag :
  - 스튜던트 t 분포
  - F 분포
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

# 7. 연속 확률변수와 확률밀도함수의 유형 - 4

<br>

**학습 내용**

- 스튜던트 t 확률분포함수
- F 확률분포함수

<br>

## 7.1 스튜던트 t 확률분포 (Student t)

<br>

- $$Q$$ : 카이제곱 확률변수, $$Q \sim \chi^2(\nu)$$
- $$Z$$ : 표준 정규분포 확률변수, $$Z \sim N(0,1)$$

- 위 두 확률변수를 이용하여 스튜던트 t 확률변수 $$T$$를 다음과 같이 정의한다.

$$
\qquad
T = {Z \over \sqrt{Q / \nu}}
$$

<br>

- $$\nu$$ : 카이제곱 확률변수의 **자유도**

<br>

- "확률변수 $$T$$가 스튜던트 t 확률분포를 따른다."

$$
\qquad
\Leftrightarrow \quad T \sim t(\nu)
$$

<br>

- 자유도 $$\nu$$ 가 커질수록 스튜던트 t 분포는 **표준정규분포로 수렴**한다.

<br>

- 스튜던트 t 확률분포함수는 구간 $$\left(- \infty, \, + \infty\right)$$ 에 대해서 정의되어 있다.

$$
\qquad
f(x) = { \Gamma({\nu+1 \over 2}) \over \sqrt{\nu \, \pi} \; \Gamma({\nu \over 2})} \left(1 + {x^2 \over \nu} \right)^{- {\nu+1 \over 2}}
$$

<br>

### 7.1.1 스튜던트 t 확률분포 함수의 평균, 분산, 표준편차

<br>

- 평균 = 0
- 분산 = $${\nu \over \nu - 2} \qquad \qquad \quad \, \Leftrightarrow \quad \nu \gt 2$$ 인 경우에만 계산 가능
- 표준편차 = $$\sqrt{\nu \over \nu - 2} \qquad \Leftrightarrow \quad \nu \gt 2$$ 인 경우에만 계산 가능

<br>

### 7.1.2 스튜던트 t 확률분포의 역할

<br>

- 스튜던트 t 분포함수는 통계에서 **신뢰구간을 계산**하는 데 매우 중요한 역할을 한다.
-  **표본에서 추출한 분산**이 **모분산**과 **크게 다를 때** (표본의 크기가 작을 때), 표준정규분포의 분위수 대신에 **스튜던트 t 분포의 분위수를 사용**해서 **신뢰구간의 하한과 상한을 계산**한다.

<br>

- 표본의 크기 = $$n$$ $$\qquad \Rightarrow \qquad$$ 자유도 $$v = n-1$$
- 표본의 크기가 커진다. $$\qquad \Rightarrow \qquad$$ 자유도가 증가한다.
- 이때, 스튜던트 t는 표준정규분포에 수렴하게 되므로, 표준정규분포의 분위수와 스튜던트 t의 분위수는 큰 차이가 없게 된다.

<br>

### 7.1.3 자유도($$\nu$$) 의 역할

<br>

- 표준정규분포 함수의 그래프와 스튜던트 t 분포 함수의 그래프 비교
  - $$\nu=1$$ 인 스튜던트 t 분포 함수 : 표준정규분포 함수와 큰 차이를 보임
  - 자유도($$\nu$$) 가 커질수록 스튜던트 t 분포함수가 표준정규분포로 수렴하는 것 확인

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img033.jpg" width="500px">
</div>

<br>

## 7.2 F 확률분포

<br>

- $$Q_1 \sim \chi^2(d_1)$$ 이고 $$Q_2 \sim \chi^2(d_2)$$ 일 때, F 확률변수 $$X$$는 다음과 같이 정의된다.

$$
\qquad
X = {Q_1 / d_1 \over Q_2 / d_2 }
$$

<br>

- $$d_1$$
  - 카이제곱 확률변수 $$Q_1$$ 의 자유도
  - F 확률변수 $$X$$의 **분자**의 자유도

- $$d_2$$
  - 카이제곱 확률변수 $$Q_2$$ 의 자유도
  - F 확률변수 $$X$$의 **분모**의 자유도

<br>

- "확률변수 $$X$$가 F 확률분포를 따른다."

$$
\qquad
\Leftrightarrow \quad X \sim F(d_1,d_2)
$$

<br>

- F 검정, 분산분석 (ANOVA) 등에 활용

<br>

- 자유도 $$d_2$$(분모의 자유도)가 커질수록 F분포는 **카이제곱 $$Q_1 / d_1$$ 로 수렴**한다.

<br>

### 7.2.1 F 확률분포함수의 평균, 분산, 최빈값

<br>

- 평균 = $${d_2 \over d_2 - 2} \qquad\qquad\,\;\quad\qquad\qquad\qquad \Leftrightarrow \quad d_2 \gt 2$$ 인 경우에만 계산 가능
- 분산 = $${2 \,d_2^2 \, \left(d_1+d_2-2\right) \over d_1 \, \left(d_2 - 4\right) \, \left(d_2 - 2\right)^2} \qquad\qquad\qquad\quad\; \Leftrightarrow \quad d_2 \gt 4$$ 인 경우에만 계산 가능
- 최빈값 (mode) = $$\left({d_1 - 2 \over d_1}\right) \, \left({d_2 \over d_2 + 2}\right) \qquad \Leftrightarrow \quad d_1 \gt 2$$ 인 경우에만 계산 가능

<br>

### 7.2.2 F 확률분포함수 시각화

<br>

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img034.jpg" width="500px">
</div>
