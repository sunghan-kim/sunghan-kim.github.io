---
title: "확률의 곱셈 법칙"
date: 2019-03-17
category:
  - Statistics
tag :
  - 조건부확률
  - 종속사건
  - 독립사건
  - 배반사건
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

# 3. 확률의 곱셈 법칙

<br>

**학습 내용**

- 확률의 곱셈
- 조건부 확률
- 독립사건, 종속사건, 배반사건의 차이

<br>

## 3.1 조건부 확률

- 확률이 0이 아닌 사건 $$A$$와 $$B$$에 대해 **사건 $$A$$가 일어났다는 전제**로 사건 $$B$$가 일어날 확률
- $$P(B \mid A)$$와 같이 표기

$$\qquad
P(B \mid A) = \frac{P(A \cap B)}{P(A)}
$$

- 위 수식 정리

$$\qquad
P(A \cap B) = P(A \mid B) P(B)
$$
<br><br>
$$\qquad
\qquad\qquad\;\, = P(B \mid A) P(A)
$$

<div style="text-align: center">
	<img src="/assets/images/lecture/FE_quant/FE/part01/ch01/img005.jpg" width="200px">
</div>

<br>

## 3.2 종속사건 vs 독립사건 vs 배반사건

### 3.2.1 종속사건 (dependent events)

- 사건 $$A$$와 $$B$$가 **종속사건**인 경우 **교집합**의 확률:

$$\qquad
P(A \cap B) \neq P(A) P(B) \quad \leftarrow \quad P(A)와\, P(B)로\, 인수분해\, 할\, 수\, 없음
$$
<br><br>
$$\qquad
P(A \cap B) = P(A \mid B) P(B)
$$
<br><br>
$$\qquad
\qquad\qquad\;\, = P(B \mid A) P(A)
$$

<br>

- 사건 $$A$$와 $$B$$가 **종속사건**인 경우 **합집합**의 확률:

$$\qquad
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$
<br><br>
$$\qquad
\qquad\qquad\;\, = P(A) + P(B) - P(A \mid B) P(B)
$$
<br><br>
$$\qquad
\qquad\qquad\;\, = P(A) + P(B) - P(B \mid A) P(A)
$$


<br>

### 3.2.2 독립사건 (independent events)

- 사건 $$A$$와 $$B$$가 **독립사건**인 경우 **교집합**의 확률:

$$\qquad
P(A \cap B) = P(A) P(B) \quad \leftarrow \quad P(A)와\, P(B)로\, 인수분해\, 할\, 수\, 있음
$$

<br>

- 사건 $$A$$와 $$B$$가 **독립사건**인 경우 **합집합**의 확률:

$$\qquad
P(A \cup B) = P(A) + P(B) - P(A) P(B)
$$

<br>

- 사건 $$A$$와 $$B$$가 **독립사건**인 경우 **조건부 확률**:

$$\qquad
P(A \mid B) = P(A)
$$
<br><br>
$$\qquad
P(B \mid A) = P(B)
$$


<br>

### 3.2.3 배반사건 (mutually exclusive events)

- 사건 $$A$$와 $$B$$가 **배반사건**이라면, **동시에 일어날 수 없다**는 의미

<br>

- 사건 $$A$$와 $$B$$가 **배반사건**인 경우 **교집합**의 확률:

$$\qquad
P(A \cap B) = 0
$$

<br>

- 사건 $$A$$와 $$B$$가 **배반사건**인 경우 **합집합**의 확률:

$$\qquad
P(A \cup B) = P(A) + P(B)
$$

<br>

- 사건 $$A$$와 $$B$$가 **배반사건**인 경우 **조건부 확률**:

$$\qquad
P(A \mid B) = 0
$$
<br><br>
$$\qquad
P(B \mid A) = 0
$$

<br>

### 3.2.4 독립사건 vs 배반사건

- 독립사건과 배반사건은 서로 **무관**의 다른 개념이다.

<br>

## 3.3 확률의 곱셈

### 3.3.1 문제 (1)

- A, B 두 반의 학생 120명을 남녀별로 구분한 표 (분할표)

||남(M)|여(F)|계|
|:---:|:---:|:---:|:---:|
|A반|35|30|65|
|B반|32|23|55|
|계|67|53|120|

<br>

**1) 120명의 집합을 표본공간으로 하여 1명을 뽑을 때 $$P(M \mid A)$$ 와 $$P(F \mid A)$$는?**

**Answer)**

$$\qquad
P(A) = \frac{65}{120}, \; P(B) = \frac{55}{120}, \; P(M) = \frac{67}{120}, \; P(F) = \frac{53}{120}
$$
<br><br>
$$\qquad
P(M \cap A) = \frac{35}{120}, \; P(F \cap A) = \frac{30}{120}
$$
<br><br>
$$\qquad
\therefore \quad P(M \mid A)
= \frac{P(M \cap A)}{P(A)}
= \frac{35}{120} \times \frac{120}{65}
= \frac{35}{65}
$$
<br><br>
$$\qquad
\therefore \quad P(F \mid A)
= \frac{P(F \cap A)}{P(A)}
= \frac{30}{120} \times \frac{120}{65}
= \frac{30}{65}
$$

<br>

**2) 120명의 집합을 표본공간으로 하여 1명을 뽑을 때 $$P(A \mid M)$$ 와 $$P(B \mid M)$$는?**

**Answer)**

$$\qquad
P(B \cap M) = \frac{32}{120}
$$
<br><br>

$$\qquad
\therefore \quad  P(A \mid M)
= \frac{P(A \cap M)}{P(M)}
= \frac{35}{120} \times \frac{120}{67}
= \frac{35}{67}
$$
<br><br>
$$\qquad
\therefore \quad P(B \mid M)
= \frac{P(B \cap M)}{P(M)}
= \frac{32}{120} \times \frac{120}{67}
= \frac{32}{67}
$$

<br>

### 3.3.2 문제 (2)

- 주머니 속에 흰 공 4개, 붉은 공 6개가 있다.
- 공을 한 개씩 두 번 꺼낼 때, 다음 각 경우에 대하여 **두 개가 모두 흰 공일 확률**을 구하여라.

<br>

**1) 처음 꺼낸 공을 다시 넣지 않는 경우**

- 사건 $$A$$ : 첫 번째에 흰 공이 나오는 사건
- 사건 $$B$$ : 두 번째에 흰 공이 나오는 사건
- 구하고자 하는 확률 $$\; = \;P(A \cap B)$$
- 확률의 곱셈 정리 적용

$$\qquad
P(A \cap B) = P(B \mid A) P(A) = \frac{3}{9} \times \frac{4}{10} = \frac{2}{15}
$$

<br>

**2) 처음에 꺼낸 공을 다시 넣는 경우**

- 이 경우 $$A$$와 $$B$$는 서로 **독립사건**이다.

$$\qquad
P(A \cap B) = P(B \mid A) P(A) = P(B) P(A) = \frac{4}{10} \times \frac{4}{10} = \frac{4}{25}
$$
