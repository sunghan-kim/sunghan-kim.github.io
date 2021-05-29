---
title: "베이즈 정리와 활용"
date: 2019-03-18
category:
  - Statistics
tag :
  - 베이즈 정리
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
> 통계 > 확률과 통계 > 확률 기초

<br>

# 4. 베이즈 정리와 활용

<br>

**학습 내용**

- 베이즈 정리 (베이즈 통계법)
- 조건부 확률

<br>

## 4.1 조건부 확률: 확률의 곱셈 법칙 적용

- 확률이 0이 아닌 사건 $$A$$와 $$B$$에 대해 **사건 $$A$$가 일어났다는 전제**로 사건 $$B$$가 일어날 확률
- $$P(B \mid A)$$와 같이 표기

$$\qquad
P(B \mid A) = \frac{P(A \cap B)}{P(A)}
$$

- 위 수식은 **확률의 곱셈 법칙**을 적용한 것이다.

<br>

- 위 수식 정리

$$\qquad
P(A \cap B) = P(A \mid B) P(B)
$$
<br><br>
$$\qquad
\qquad\qquad\;\, = P(B \mid A) P(A)
$$

<br>

## 4.2 베이즈 정리

- 위 수식을 통해 **"베이즈 정리"**를 도출해 낼 수 있다.

$$\qquad
P(A \mid B) P(B) = P(B \mid A) P(A)
$$

<br>

- 베이즈 정리를 다음과 같이 변형하여 사용할 수 있다.

<br>

1. **$$P(A \mid B)$$를 구하기 어려울 때**

  - 베이즈 정리를 이용해 $$P(B \mid A)$$ 값을 통해 $$P(A \mid B)$$의 값을 계산할 수 있다.


$$\qquad\qquad
P(A \mid B) = \frac{P(B \mid A) P(A)}{P(B)}
$$

<br>

2. **$$P(B)$$를 구하기 어려울 때**

  - 베이즈 정리를 이용해 아래와 같이 $$P(B)$$를 전개하여 계산

$$\qquad\qquad
P(A \mid B) = \frac{P(B \mid A) P(A)}{P(B \mid A) P(A) + P(B \mid A^c) P(A^c)}
$$

<br>

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch01/img006.jpg" width="600px">
</div>

<br>

### 4.2.1 문제 (1)

- 1000개의 동전이 있음
- 그 중 1개의 동전은 양쪽이 앞면(H)인 "비정상" 동전
- 나머지 999개는 앞(H)/뒤(T) 면이 있는 "정상적"인 동전
- 임의의 동전 한 개를 뽑아서 10번 던져보니 항상 앞면만 나옴
- 이 동전이 바로 양면이 H인 동전인 확률은?

<br>

**Answer)**

- 사건 $$A$$ : 뽑은 동전이 비정상 동전(양면이 H인 동전)일 사건
- 사건 $$A^c$$ : 뽑은 동전이 정상 동전일 사건
- 사건 $$B$$ : 뽑은 동전을 10번 던져서 항상 앞면만 나온 사건

$$\qquad
P(B \mid A) = 1
$$

$$\qquad
P(B \mid A^c) = (\frac{1}{2})^{10}
$$

$$\qquad
P(A) = \frac{1}{1000}
$$

$$\qquad
P(A^c) = \frac{999}{1000}
$$

<br>

- **확률 $$P(A \mid B)$$**를 계산 (10번 던져 항상 앞면이 나왔는데 이 동전이 비정상 동전일 확률)

$$\qquad
P(A \mid B) = \frac{P(B \mid A) P(A)}{P(B \mid A) P(A) + P(B \mid A^c) P(A^c)}
$$

$$\qquad
\qquad\qquad\, = \frac{1 \times \frac{1}{1000}}{1 \times \frac{1}{1000} + (\frac{1}{2})^{10} \times \frac{999}{1000}}
$$

$$\qquad
\qquad\qquad\, \approx 0.506
$$

<br>

### 4.2.2 문제(2)

- 변종 인플루엔자가 돌고 있다.
- 전체 감염자의 확률은 3%
- 새로운 진단 방법이 개발 됐는데 실제 감염자 중에서 98%를 정확하게 양성(+)으로 진단하고 또한 실제 비감염자 중에서 95%를 정확하게 음성(-)으로 진단할 수 있음
- 본인이 이 검사를 받아봤는데 결과가 양성(+)으로 나옴
- 실제 이 변종 인플루엔자에 걸렸을 확률은?

<br>

**Answer)**

- 사건 $$D$$ : 변종 인플루엔자에 걸릴 사건
- 사건 $$D^c$$ : 변종 인플루엔자에 걸리지 않은 사건

- **민감도**(병에 걸렸을 때 양성으로 판단할 확률) : $$P(+ \mid D) = 0.98$$
- **특이도**(병에 걸리지 않았을 때 음성으로 판단할 확률) : $$P(- \mid D^c) = 0.95$$

$$\qquad
\Rightarrow P(+ | D^c) = 1 - P(- \mid D^c) = 0.05 \quad \leftarrow \quad
$$ 병에 걸리지 않았을 때 양성으로 판단할 확률

- **발병률**(병에 걸릴 확률) : $$P(D) = 0.03$$

<br>

- **$$P(D \mid +)$$** 계산 (양성으로 나왔는 데 실제 병에 걸렸을 확률)

$$\qquad
P(D \mid +) = \frac{P(+ \mid D) P(D)}{P(+ \mid D) P(D) + P(+ \mid D^c) P(D^c)}
$$

$$\qquad
\qquad\qquad\, = \frac{0.98 \times 0.03}{0.98 \times 0.03 + 0.05 \times 0.97}
$$

$$\qquad
\qquad\qquad\, \approx 0.377
$$
