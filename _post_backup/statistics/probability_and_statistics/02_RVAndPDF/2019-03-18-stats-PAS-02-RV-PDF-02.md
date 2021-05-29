---
title: "이산확률 Ⅱ"
date: 2019-03-18
category:
  - Statistics
tag :
  - 베르누이 확률분포
  - 이항 확률분포
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

# 2. 이산 확률변수와 확률분포함수의 유형 - 2

<br>

**학습 내용**

- 베르누이 확률분포
- 이항 확률분포

<br>

## 2.1 베르누이 확률분포 (Bernoulli)

- 동전 던지기와 같은 상황에 사용할 수 있는 확률분포 함수
- 동전 던지기의 결과는 앞면, 뒷면 2가지가 있다.
- 앞면과 뒷면이 나올 확률을 각각 $${1 \over 2}$$이다.

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img001.jpg" width="300px">
</div>

<br>

**일반화**

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img002.jpg" width="400px">
</div>

<br>

### 2.1.1 베르누이 시행

- 두개의 가능한 값이 있음
- ex) 1 또는 0, 동전의 앞면(H) 또는 뒷면(T), "성공" 또는 "실패"
- 베르누이 시행에서
  - $$P(X = 1) = p$$
  - $$P(X = 0) = 1 - p$$  



  <br>

- "확률변수 X가 베르누이 확률분포를 따른다."

  $$
  \qquad
  \Leftrightarrow \quad X \sim Ber(p)
  $$

<br>

### 2.1.2 베르누이 확률분포함수

<br>

$$
\qquad
P(x) = p^x \left(1 - p\right)^{1-x}
$$

<br>

### 2.1.3 베르누이 확률변수의 평균, 분산, 표준편차

<br>

1) **평균**  


$$
\qquad
1 \, P(1) + 0 \, P(0) = P(1) = p
$$
<br><br>

2) **분산**  


$$
\qquad
\{1^2 \, P(1) + 0^2 \, P(0)\} - p^2 = P(1) - p^2 = p - p^2 = p\,(1-p)
$$
<br><br>

3) **표준편차**  


$$
\qquad
\sqrt{p\,(1-p)}
$$
<br><br>

## 2.2 이항 확률분포 (Binomial)

- 동전을 여러 번 던지는 상황
- 이항 확률변수 $$X_{bin}$$은 0 또는 1의 값을 갖는 $$n$$개의 **독립적**인 베르누이 확률변수 $$X_{Ber}$$를 더한 것

$$
\qquad
X_{bin} = X_{Ber} + X_{Ber} + \cdots + X_{Ber}
$$

- ex) 동전 하나를 $$n$$번 던져서 앞면(H)이 나온 횟수를 집계 ($$n$$회 시행하여 "성공"한 횟수를 더한다.)

<br>

- "확률변수 $$X$$가 이항 확률분포를 따른다"

$$
\qquad
\Leftrightarrow \quad X \sim Bin(n, p)
$$

<br>

### 2.2.1 이항 확률 분포함수

<br>

$$
\qquad
P(x) = \binom{n}{x} p^x \left(1-p\right)^{n-x}
$$

<br>

- $$p$$
  - 개개 베르누이 확률변수의 값이 1과 같을 확률  

- $$x$$
  - $$n$$사이의 숫자이어야 한다.

$$
\qquad\qquad
0 \leq x \leq n
$$

<br>

- $$\binom{n}{x}$$
  - 조합

$$
\qquad\qquad
{n! \over x! (n-x)!}
$$

<br>

### 2.2.2 이항 확률변수의 평균, 분산, 표준편차

- 이항 확률변수의 **정의**를 그대로 적용하여 평균, 분산, 표준편차를 구하는 것이 이항 확률분포함수를 사용해서 구하는 것보다 **쉽다**.

<br>

1) **평균**

- 개별 베르누이 확률변수의 평균의 합

$$
\qquad
\begin{align*}
E[X_{bin}] &= E[X_{Ber}] + \cdots + E[X_{Ber}] &= n \, E[X_{Ber}] \\
\\
&= n \, p
\end{align*}
$$

<br><br>

2) **분산**

- 개별 베르누이 확률변수의 분산의 합
- 개별 베르누이 확률변수는 서로 독립적이기 때문에 공분산 항이 필요 없음

$$
\qquad
\begin{align*}
Var(X_{bin}) &= Var(X_{Ber}) + \cdots + Var(X_{Ber}) \\
\\
&= n \, Var(X_{Ber}) \\
\\
&= n \, p \, (1 - p)
\end{align*}
$$

<br><br>

3) **표준편차**  


$$
\qquad
\sqrt{n \, p (1-p)}
$$
<br><br>



### 2.2.3 이항 확률분포의 예

- $$n=10,\; p=0.5$$
- 평균 = 5

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img003.jpg" width="400px">
</div>

<br>

- $$n=10,\; p=0.3$$
- 평균 = 3

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img004.jpg" width="400px">
</div>

<br>

- $$n=10,\; p=0.7$$
- 평균 = 7

<div style="text-align: left; margin-left: 10px;">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img005.jpg" width="400px">
</div>

<br>

### 2.2.4 이항 확률변수의 합

- 서로 독립적인 확률변수 $$X$$와 $$Y$$가 다음과 같이 이항 확률 분포를 따른다고 하자.

$$
\qquad
X \sim Bin(n,\, p)
$$

$$
\qquad
Y \sim Bin(m,\, p)
$$

- 그러면, $$X + Y$$는 또 다른 이항 확률변수이다.

$$
\qquad
X + Y \sim Bin(n+m, \, p)
$$

- $$p$$는 변하지 않고 같다.

<br>

**증명**  


$$
\qquad
X + Y = \{X_{Ber} + X_{Ber} + \cdots + X_{Ber}\} + \{X_{Ber} + X_{Ber} + \cdots + X_{Ber}\}
$$

$$\qquad\qquad\qquad\qquad\qquad\quad n개 \qquad\qquad\qquad\qquad\qquad\qquad m개$$

$$
\qquad
\Rightarrow X + Y \sim Bin(n + m,\, p)
$$

<br>

### 2.2.5 이항 확률분포의 문제

- 장마 기간에 일일 강우 확률은 30%이다.
- 향후 5일간 날씨에 대한 질문에 답하여라.

<br>

**1) 비가 한 번도 오질 않을 확률은?**  


$$
\qquad
\begin{align*}
P(0) &= \binom{5}{0} \left(0.3\right)^0 \, \left(1 - 0.3\right)^{5-0} \\
\\
&= {5! \over 0! 5!} 0.7^{5} = 0.7^5 \\
\\
&= 0.168
\end{align*}
$$
<br>

$$\qquad \Rightarrow \quad$$ 대략 16.8%

<br>

**2) 비가 정확하게 2번 올 확률은?**  


$$
\qquad
\begin{align*}
P(2) &= \binom{5}{2} \left(0.3\right)^2 \, \left(1 - 0.3\right)^{5-2} \\
\\
&= {5! \over 2! 3!} 0.3^2 \, 0.7^{3} \\
\\
&= 10 \times 0.3^2 \, 0.7^{3} \\
\\
&= 0.309
\end{align*}
$$
<br>

$$\qquad \Rightarrow \quad$$ 대략 30.9%

<br>

**3) 비가 3회 이하 올 확률은?**


$$
\qquad
\begin{align*}
P(X \leq 3) &= P(0) + P(1) + P(2) + P(3) \\
\\
&= \binom{5}{0} \left(0.3\right)^0 \, \left(1 - 0.3\right)^{5-0} + \binom{5}{1} \left(0.3\right)^1 \, \left(1 - 0.3\right)^{5-1} + \binom{5}{2} \left(0.3\right)^2 \, \left(1 - 0.3\right)^{5-2} + \binom{5}{3} \left(0.3\right)^3 \, \left(1 - 0.3\right)^{5-3} \\
\\
&= 1 \times 1 \times 0.7^5 + 5 \times 0.3 \times 0.7^4 + 10 \times 0.3^2 \times 0.7^3 + 10 \times 0.3^3 \times 0.7^2 \\
\\
&= 0.16807 + 0.36015 + 0.3087 + 0.1323 \\
\\
&= 0.96922
\end{align*}
$$
<br>

$$\qquad \Rightarrow \quad$$ 대략 96.9%

<br>

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch02/img006.jpg" width="400px">
</div>
