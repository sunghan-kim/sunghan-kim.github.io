---
title: "조건문 if"
date: 2019-03-12
category:
  - R
tag :
  - if문
  - 조건문
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
> R > Programming > Function

<br>

# 2. 조건문 if

## 2.1 조건문의 구조

### 2.1.1 조건문의 구조 (1)
- `if ~ else`
- 논리형 스칼라 : 데이터가 1개인 논리형 데이터
```R
조건 <- 논리형 스칼라
```
```R
if (조건) {
	조건이 맞을 때 실행해야 할 내용
} else {
	조건이 맞지 않을 때 실행해야 할 내용
}
```

<br>

- 조건문 구조 (1)의 첫 번째 예
```R
> x <- 5
```
```R
> if (x > 5) {
	x <- x + 3
 } else {
	x <- x - 3
 }
```
```R
> x
[1] 2
```

<br>

- 조건문 구조 (1)의 두 번째 예
```R
> x <- 10
```
```R
> if (x > 5) {
	x <- x + 3
 } else {
	x <- x - 3
 }
```
```R
> x
[1] 13
```

<br>

### 2.1.2 조건문의 구조 (2)

- `if` 만 있는 경우
```R
if (조건) {
	조건이 맞을 때 실행해야 할 내용
}
```

<br>

### 2.1.3 조건 확인

- 관계 연산과 논리 연산을 통해 조건을 판단
- if 내의 조건은 1개만 가능
- `any()`, `all()` 함수와 `||`, `&&` 연산자가 유용

<br>

- 예시 1
```R
> c(T,T,T,T)
[1] TRUE TRUE TRUE TRUE
```
```R
> all(c(T,T,T,T))
[1] TRUE
```
```R
> if (all(c(T,T,T,T))) {
	print("all True!")
 }
[1] "all True!"
```

<br>

- 예시 2
```R
> c(F,F,F,F)
[1] FALSE FALSE FALSE FALSE
```
```R
> any(c(F,F,F,F))
[1] FALSE
```
```R
> if (any(c(F,F,F,F))) {
	print("any True!")
 }
```

<br>

- 예시 3
```R
> c(T,T,T) || c(F,F,F,F)
[1] TRUE
```
```R
> if (c(T,T,T) || c(F,F,F,F)) {
	print( "works!")
 }
[1] "works!"
```

<br>

### 2.1.4 조건문의 구조 (3)

- `if ~ else if ~ else`
- `else` 다음에 `if`를 중첩해서 작성
```R
if (조건1) {
	조건1이 맞을 때 실행해야 할 내용
} else if (조건2) {
	조건1은 맞지 않고 조건2는 맞을 때 실행해야 할 내용
} else {
	모든 조건에 맞지 않을 때 실행해야 할 내용
}
```

<br>

- 조건문 구조 (3) 의 첫 번째 예시
```R
> x <- 6
```
```R
> if (x > 5) {
	x <- x + 3
 } else if (x == 0) {
	x <- x
 } else {
	x <- x - 3
 }
```
```R
> x
[1] 9
```

<br>

- 조건문 구조 (3) 의 두 번째 예시
```R
> x <- 0
```
```R
> if (x > 5) {
	x <- x + 3
 } else if (x == 0) {
	x <- x
 } else {
	x <- x - 3
 }
```
```R
> x
[1] 0
```

<br>

- 조건문 구조 (3) 의 세 번째 예시
```R
> x <- 2
```
```R
> if (x > 5) {
	x <- x + 3
 } else if (x == 0) {
	x <- x
 } else {
	x <- x - 3
 }
```
```R
> x
[1] -1
```
