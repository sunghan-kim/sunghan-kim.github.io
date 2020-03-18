---
title: "확률의 덧셈 법칙"
date: 2019-03-16
category:
  - Statistics
tag :
  - 확률의 덧셈
  - 배반사건
  - 여사건
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

# 2. 확률의 덧셈 법칙

<br>

**학습 내용**

- 확률의 덧셈
- 배반사건
- 여사건

<br>

## 2.1 확률의 덧셈

- 어떤 사건 $$A$$와 $$B$$에 대해서:

$$\qquad
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch01/img001.jpg" width="200px">
</div>

<br>

- $$A$$와 $$B$$가 **배반사건**인 경우 ($$A \cap B = \emptyset $$):

$$\qquad
P(A \cup B) = P(A) + P(B)
$$

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch01/img002.jpg" width="250px">
</div>

<br>

- $$A$$, $$B$$, $$C$$가 **배반사건**인 경우 ($$A \cap B = \emptyset, A \cap C = \emptyset, B \cap C = \emptyset $$):

$$\qquad
P(A \cup B \cup C) = P(A) + P(B) + P(C)
$$

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch01/img003.jpg" width="350px">
</div>

<br>

## 2.2 여사건의 확률

- 어떤 사건 $$A$$의 확률과 **여사건** $$\,A^c$$의 확률 사이에는 다음 관계가 성립:

$$\qquad
A \cup A^c = S \quad\Rightarrow \quad P(A) + P(A^c) = 1
$$
<br><br>
$$\qquad
\qquad\qquad\quad\; \quad\quad\quad\, P(A) = 1 - P(A^c)
$$

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch01/img004.jpg" width="250px">
</div>

<br>

## 2.3 문제

### 2.3.1 문제 (1)

- 다섯 개의 동전을 던졌을 때, 적어도 한 개가 앞면이 나올 확률은?

**Answer)**

- 사건 $$A$$ : 적어도 한 개가 앞면이 나오는 사건
- 사건 $$A^c$$ : 모두 뒷면이 나오는 사건

$$\qquad
P(A^c) = \frac{1}{2^5} = \frac{1}{32}
$$

- $$P(A) + P(A^c) = 1$$ 관계를 적용하여 사건 $$A$$ 확률 계산

$$\qquad
P(A) = 1 - P(A^c) = 1 - \frac{1}{32} = \frac{31}{32}
$$

<br>

### 2.3.2 문제 (2)

- 하나의 주사위를 던질 때, 짝수의 눈 또는 3 이상의 눈이 나올 확률은?

**Answer)**

- 사건 $$A$$ : 짝수의 눈이 나오는 사건

$$\qquad
A = \{2, 4, 6\}
$$

- 사건 $$B$$ : 3 이상의 눈이 나오는 사건

$$\qquad
B = \{2, 4, 5, 6\}
$$

- 짝수 **또는** 3 이상의 눈이 나오는 사건

$$\qquad
A \cup B = \{2, 3, 4, 5, 6\}
$$

- 확률의 **수학적 정의**를 적용하여 확률 계산

$$\qquad
A \cup B = \frac{기대하는\, 것이\, 일어나는\, 경우의\, 수}{일어날\, 수\, 있는\, 모든\, 경우의\, 수}
         = \frac{5}{6}
$$

<br>

- 확률의 **덧셈 법칙**을 적용하여 확률 계산

$$\qquad
P(A) = \frac{3}{6},\; P(B) = \frac{4}{6},\; P(A \cap B) = P(\{4, 6\}) = \frac{2}{6}
$$

$$\qquad
\rightarrow P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

$$\qquad
\qquad\qquad\quad\;\;\, = \frac{3}{6} + \frac{4}{6} - \frac{2}{6} = \frac{5}{6}
$$

<br>  

### 2.3.3 문제 (3)

- 100명의 학생 중 혈액형이 O형, A형, B형, AB형인 학생이 각각 29명, 41명, 28명, 12명이다.
- 이 중에서 임의로 한명을 뽑을 때, O형이거나 A형일 확률은?

**Answer)**

- 확률의 **덧셈 법칙** 적용

$$\qquad
P(O) = \frac{29}{100},\; P(A) = \frac{41}{100},\; P(O \cap A) = P(\emptyset) = 0 \;\leftarrow 배반사건!
$$

$$\qquad
\therefore \quad P(O \cup A) = P(O) + P(A) = \frac{29}{100} + \frac{41}{100} = \frac{7}{10}
$$
