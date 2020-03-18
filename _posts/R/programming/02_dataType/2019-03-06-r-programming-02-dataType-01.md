---
title: "R의 데이터 유형"
date: 2019-03-06
category:
  - R
tag :
  -
sidebar:
  nav: sidebar-r-programming
mathjax: "true"
author_profile: false
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
header:
  overlay_image: /assets/images/r.jpg
  overlay_filter: 0.5
comments: true
---
> R > Programming > Data Type

<br>


# 1. R의 데이터 유형

## 1.1 R의 기본 데이터 유형
<div style="text-align:center;">
<img src="/assets/images/lecture/FE_quant/r/part01/ch02/img001.jpg" width="600px"/>
</div>
### 1.1.1 벡터

- 한 개 이상의 데이터 묶음
- **원자 벡터**, **리스트**가 있다.

### 1.1.2 NULL

- 데이터가 없음
- 있는 데이터를 없다고 표시할 때 NULL을 사용

### 1.1.3 원자 벡터 (Atomic Vector)

- 모두 같은 종류의 데이터를 가지고 있는 데이터 묶음
- 같은 종류 → atomic
- 논리형, 숫자형(정수형, 실수형), 글자형이 있음

**1) 논리형**

- True, False

**2) 숫자형**

- 정수형과 실수형이 있음
- R에서는 실수형을 기본으로 함 (정수형은 따로 지정을 해줘야 함)
- 정수형은 실수형에 포함됨

**3) 글자형**

- 문자열 형태

### 1.1.4 리스트

- 다양한 종류의 데이터 유형을 가지는 데이터 묶음
