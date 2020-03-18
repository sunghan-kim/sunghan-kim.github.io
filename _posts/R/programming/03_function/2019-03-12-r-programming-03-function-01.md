---
title: "함수의 구조 및 작성"
date: 2019-03-12
category:
  - R
tag :
  - R 함수
  - 입력 인자
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

# 1. 함수의 구조 및 작성

## 1.1 함수의 구조

### 1.1.1 함수 선언

- 함수를 선언할 때의 모양은 다음과 같다.
```r
함수명 <- function(인자1, 인자2=기본값){
	동작할 내용
}
```

- 1을 더하는 함수 `add_one` 작성
```R
> add_one <- function(x){
	x <- x + 1
	return(x)
 }
```

- `add_one` 함수 실행
```R
> add_one(10)
[1] 11
```

<br>

### 1.1.2 입력 인자가 있는 함수

<br>

- **함수의 입력 인자의 2가지 종류**
  1.  사용할 데이터
  2.  동작의 세부 사항을 결정하는 설정들

<br>

- `add_some` 함수 작성
```R
> add_some <- function(x, some = 1){
   x <- x + some
   return(x)
 }
```

- `x` : 사용할 데이터
- `some=1` : 동작의 세부 사항을 결정하는 설정

<br>

- `add_some` 함수 실행
```R
> add_some(10)
[1] 11
```
```R
> add_some(10, some = 3)
[1] 13
```

<br>

- `add_some` 함수 확인 (`args()` 함수 이용)
```R
> args(add_some)
function (x, some = 1)
NULL
```

<br>

### 1.1.3 입력 인자가 없는 함수

- 입력 인자 없이 출력만 있는 함수도 가능 (괄호 안에 아무것도 입력하지 않음)

<br>

- 함수 `one_o_ten` 작성
```R
> one_to_ten <- function(){
   ot <- 1:10
   return(ot)
 }
```

<br>

- 함수 `one_o_ten` 실행
```R
> one_to_ten()
 [1]  1  2  3  4  5  6  7  8  9 10
```

<br>

- 인자 없는 함수의 예 : `getwd()`
```R
> getwd()
[1] "C:/shkim/FinancialEngineering/firstProject"
```

<br>

## 1.2 전역과 지역

- **전역변수** : global

- **지역변수** : local, 함수 내부에 있는 변수 (중괄호 안에 있는 것들)

<br>

### 1.2.1 지역변수를 외부에서 사용 (불가능)

- 함수내부에서 정의된 지역변수를 전역에서 사용하는 것은 불가능하다.
```R
> one_to_ten_ot <- function(){
   ot <- 110
   return(ot)
 }
```
```R
> ot
Error: object 'ot' not found
```

- `ot`는 함수 내부에서 정의된 지역변수이므로 전역변수 `ot`는 존재하지 않는다.

<br>

### 1.2.2 전역변수를 지역에서 사용 (가능)

- 전역변수를 함수내부에서 사용하는 것은 가능하다.
```R
> a <- 1
```
```R
> add_a <- function(x){
   return(x + a)
 }
```
```R
> add_a(10)
[1] 11
```

<br>

### 1.2.3 전역변수 사용 대신 인자 사용

- 함수 작성 시 함수 내부에서 전역변수를 사용하게 하는 방법은 추천하지 않는다.
- 대신 인자를 통해 전달하는 것을 추천
- 인자로 전달한 데이터는 인자 이름으로 함수 내부에서만 사용할 수 있음

<br>

- `add_b` 함수 작성
```R
> add_b <- function(x, b){
   return(x + b)
 }
```

<br>

- `add_b` 함수 사용 (1)
```R
> add_b(13,4)
[1] 17
```

<br>

- `add_b` 함수 사용 (2)
```R
> k <- 8
```
```R
> add_b(13,k)
[1] 21
```

<br>

### 1.2.4 알맞은 자료형의 입력 인자 사용

- 함수 내부 동작을 잘 확인해서 적절한 동작을 수행할 수 있는 자료형의 입력 인자 사용
```R
> add_b("k",k)
Error in x + b : non-numeric argument to binary operator
```
