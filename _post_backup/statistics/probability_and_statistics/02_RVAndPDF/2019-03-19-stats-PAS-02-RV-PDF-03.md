---
title: "이산확률 Ⅲ"
date: 2019-03-19
category:
  - Statistics
tag :
  - 푸아송 확률분포
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

# 3. 이산 확률변수와 확률분포함수의 유형 - 3

<br>

**학습 내용**

- 푸아송 확률분포
- 이항과 푸아송의 관계

<br>

## 3.1 푸아송 확률분포 (Poisson)

- 푸아송 확률분포는 프랑스의 과학자 Simeon Poisson의 이름에서 유래
- 일정 시간 또는 공간에서 발생하는 사건(성공)의 횟수(count)에 대한 이산 확률분포
- ex) 시간 당 수신하는 이메일의 개수
- ex) 특정 지역(국가)의 년간 지진 발생 횟수
- ex) 초콜릿 침 쿠키에 박힌 초콜렛 조각의 개수

<br>

- "확률변수 $$X$$가 푸아송 확률분포를 따른다."

$$
\qquad
\Leftrightarrow \quad X \sim Pois(\lambda)
$$

<br>

### 3.1.1 푸아송 확률분포함수

- 푸아송 확률분포함수는 아래와 같다.

$$
\qquad
P(x) = {\lambda^x \, e^{-\lambda} \over x!}
$$

<br>

- $$\lambda$$
  - 유일한 파라미터
  - 양의 수치이어야 함
  - 한 단위 시간 또는 공간에서 발생하는 사건(성공) 횟수의 평균
  - 발생률 or 성공률

- $$x$$
  - 0 이상의 숫자 ($$0 \leq x$$)

<br>

### 3.1.2 푸아송 확률변수의 평균, 분산, 표준편차

<br>

- 푸아송 확률변수의 평균과 분산은 동일

<br>

1) **평균**  


$$
\qquad
E[X_{Pois}] = \lambda
$$

<br><br>

2) **분산**  


$$
\qquad
Var(X_{Pois}) = \lambda
$$

<br><br>

3) **표준편차**  


$$
\qquad
\sqrt{\lambda}
$$

<br>

### 3.1.3 푸아송 확률분포함수의 예

<br>

- $$\lambda = 2$$

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img007.jpg" width="400px">
</div>

<br>

- $$\lambda = 4$$

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img008.jpg" width="400px">
</div>

<br>

- $$\lambda = 6$$

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img009.jpg" width="400px">
</div>

<br>

- $$\lambda$$가 커짐에 따라 평균이 오른쪽으로 이동하는 것 확인

<br>

## 3.2 푸아송과 이항

- 푸아송과 이항은 이산확률은 나타냄

$$\qquad \rightarrow$$ 이항 확률변수의 평균 $$\quad = \quad n \, p$$

$$\qquad \rightarrow$$ 푸아송 확률변수의 평균 $$\quad = \quad \lambda$$

<br>

- 평균 일치 (**$$n\,p = \lambda$$**) 조건을 **유지**하면서 이항 확률의 $$n$$을 키우고 ($$n \uparrow$$) 동시에 $$p$$를 줄임 ($$p \downarrow$$)

$$\qquad \rightarrow$$ 이항 확률은 푸아송 확률에 수렴한다.

$$\qquad \Leftrightarrow \; p = {\lambda \over n}$$과 같이 선택한다는 의미

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img010.jpg" width="150px">
</div>

<br>

### 3.2.1 푸아송 확률분포함수와 이항 확률분포함수 비교

<br>

**1) 이항 확률분포함수 ($$n=10, \; p = 0.5$$)**

- 평균 : $$n \times p = 10 \times 0.5 = 5$$

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img011.jpg" width="400px">
</div>

<br>

**2) 이항 확률분포함수 ($$n=20, \; p = 0.25$$)**

- $$n$$을 키우고, $$p$$를 줄임
- 평균을 동일 : $$n \times p = 20 \times 0.25 = 5$$
- 그래프는 조금 더 납작해짐

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img012.jpg" width="400px">
</div>

<br>

**3) 이항 확률분포함수 ($$n = 100, \; p = 0.05 $$)**

- $$n$$을 더 키우고, $$p$$를 더 줄임
- 평균은 동일 : $$n \times p = 100 \times 0.05 = 5$$
- 그래프는 더 납작해짐

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img013.jpg" width="400px">
</div>

<br>

**4) 푸아송 확률분포함수 ($$\lambda = 5$$)**

- 이항 확률분포의 $$n$$을 계속 키우고, $$p$$를 계속 줄여가면 평균값이 동일한 푸아송 확률분포함수의 모양과 같아진다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img014.jpg" width="400px">
</div>

<br>

## 3.3 푸아송 확률분포 문제

<br>

### 3.3.1 문제

- 원자력 발전소에서 최근 5년간 2회의 shutdown급의 기술 문제 발생
- 다음 물음에 답하여라.

<br>

**1) 앞으로 1년간 한번도 shutdown급의 기술 문제가 없을 확률은?**

- 단위가 되는 시간의 구간 : 1년
- $$\lambda = {2 \over 5} = 0.4$$ : 5년간 shutdown이 발생한 사건 횟수의 평균

<br>
$$
\qquad
\therefore \quad P(0) = {0.4^0 \, e^{-0.4} \over 0!} = e^{-0.4} = 0.6703
$$
<br>

$$\qquad \Rightarrow \quad$$ 대략 67%

<br>

**2) 앞으로 1년간 한번 이상 shoutdown급의 기술 문제가 발생할 확률?**

- $$P(1) + P(2) + P(3) + \cdots$$
- 계산하기 어렵다...

$$\qquad \rightarrow \quad$$ 여사건의 확률을 $$P(0)$$을 사용하여 계산

<br>
$$
\qquad
1 - P(0) = 1 - 0.6703 = 0.3297
$$
<br>

$$\qquad \Rightarrow \quad$$ 대략 33%

<br>

**3) 앞으로 3년간 한번도 shutdown급의 기술 문제가 없을 확률은?**

- $$\lambda$$는 단위 시간 안에 발생하는 사건의 평균 횟수
- 1년의 $$\lambda =0.4$$

$$\qquad \rightarrow \quad $$시간이 3년 증가했으므로 $$\lambda = 0.4 \times 3 = 1.2$$ 를 적용

<br>
$$
\qquad
P(0) = {1.2^0 \, e^{-1.2} \over 0!} = e^{-1.2} = 0.301
$$
<br>

$$\qquad \Rightarrow \quad$$ 대략 30%

<br>

**4) 앞으로 3년간 1~2회 shutdown급의 기술 문제가 발생할 확률은?**

- $$\lambda = 1.2$$

<br>

$$
\qquad
\begin{align*}
P(1 \leq X \leq 2) &= P(1) + P(2) \\
\\
&= {1.2^1 \, e^{-1.2} \over 1!} + {1.2^2 \, e^{-1.2} \over 2!} \\
\\
&= 0.578

\end{align*}
$$

<br>

$$\qquad \Rightarrow \quad$$ 대략 57.8%
