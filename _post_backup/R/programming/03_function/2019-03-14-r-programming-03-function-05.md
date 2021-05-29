---
title: "apply 계열 함수"
date: 2019-03-14
category:
  - R
tag :
  - apply 함수
  - lapply 함수
  - sapply 함수
  - tapply 함수
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

# 5. apply 계열 함수

- apply 계열(family) 함수 : R에서 벡터 연산을 지원하는 함수
- apply 함수를 다른 사람들이 작성해 둔 것을 이해하는 데에 초첨을 맞춤


<br>

## 5.1 apply

### 5.1.1 apply 함수

- 벡터(ex. 메트릭스)에 대한 연산 수행

- `apply` 함수의 입력 인자 확인
```R
> args(apply)
function (X, MARGIN, FUN, ...)
NULL
```

- `X` : 벡터 (ex. 메트릭스)
- `MARGIN` : 방향 (**1**=행방향, **2**=열방향, **1:2**=행과 열 방향)
- `FUN` : Function, 계산을 할 함수

<br>

- apply 함수를 for문을 빠르게하는 것 정도로 이해
- 대부분의 for문은 데이터를 반복해서 계산함
- 그때 한꺼번에 할 수 있는 부분에 apply 함수 사용

### 5.1.2 apply 함수 예시

- 5x6 메트릭스 생성
```R
> mtrx <- matrix(1:30, nrow = 5, ncol = 6)
> mtrx
       [,1] [,2] [,3] [,4] [,5] [,6]
[1,]    1    6   11   16   21   26
[2,]    2    7   12   17   22   27
[3,]    3    8   13   18   23   28
[4,]    4    9   14   19   24   29
[5,]    5   10   15   20   25   30
```

<br>

- `apply` 함수 사용 (1)
```R
> apply(mtrx, 1, sum)
[1]  81  87  93  99 105
```

- `mtrx`의 데이터를 행방향(`1`)으로 더한(`sum`) 값을 각각 보여줌

<br>

- `apply` 함수 사용 (2)
```R
> apply(mtrx, 2, sum)
[1]  15  40  65  90 115 140
```

- `mtrx`의 데이터를 열방향(`2`)으로 더한(`sum`) 값을 각각 보여줌

<br>

### 5.1.3 apply 함수의 FUN 입력 인자

- `apply` 함수는 세번째 입력 인자로 함수 이름을 받음 (괄호가 포함된 함수 대신)
- `FUN` 입력 인자로 직접 정의한 함수 사용 가능
```R
> div <- function(x) x/2
> apply(mtrx, 1:2, div)
       [,1] [,2] [,3] [,4] [,5] [,6]
[1,]  0.5  3.0  5.5  8.0 10.5 13.0
[2,]  1.0  3.5  6.0  8.5 11.0 13.5
[3,]  1.5  4.0  6.5  9.0 11.5 14.0
[4,]  2.0  4.5  7.0  9.5 12.0 14.5
[5,]  2.5  5.0  7.5 10.0 12.5 15.0
```

<br>

**익명 함수**

- 이름 없이 함수를 정의하여 직접 사용
```R
> apply(mtrx, 1:2, function(x) x/2)
       [,1] [,2] [,3] [,4] [,5] [,6]
[1,]  0.5  3.0  5.5  8.0 10.5 13.0
[2,]  1.0  3.5  6.0  8.5 11.0 13.5
[3,]  1.5  4.0  6.5  9.0 11.5 14.0
[4,]  2.0  4.5  7.0  9.5 12.0 14.5
[5,]  2.5  5.0  7.5 10.0 12.5 15.0
```

<br>

## 5.2 lapply

### 5.2.1 lapply 함수

- 리스트에 apply를 하여 결과를 리스트로 제공
- `lapply` 함수의 입력 인자 확인
```R
> args(lapply)
function (X, FUN, ...)
NULL
```

- `lapply` 함수는 `apply` 함수와 달리 방향 입력 인자(`MARGIN`)이 없음

<br>

### 5.2.2 lapply 함수 예시

- 리스트 생성
```R
> l <- list(a = 1:10, b = 11:20)
> l
$a
 [1]  1  2  3  4  5  6  7  8  9 10
$b
 [1] 11 12 13 14 15 16 17 18 19 20
```

- 2개의 주머니 `a`, `b` 에 각각 10개씩의 데이터가 들어있음

<br>

- `lapply` 함수 사용 (1)
```R
> lapply(l, mean)
$a
[1] 5.5
$b
[1] 15.5
```

- 리스트내의 주머니별로 평균(`mean`)값 계산
- 계산 결과도 리스트로 반환

<br>

- `lapply` 함수 사용 (2)
```R
> lapply(l, sum)
$a
[1] 55
$b
[1] 155
```

- 리스트내의 주머니별 합계(`sum`)값 계산

<br>

- `lapply` 함수 사용 (3)
- 익명 함수 사용
```R
> lapply(l, function(x) x/2)
$a
 [1] 0.5 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0
$b
 [1]  5.5  6.0  6.5  7.0  7.5  8.0  8.5  9.0  9.5 10.0
```

- 리스트의 각 주머니안의 모든 데이터들에 대해 2로 나누는 익명 함수 연산 수행

<br>

### 5.2.3 데이터프레임에 lapply 함수 사용

- 데이터프레임은 특별한 형태의 리스트
- 데이터프레임은 리스트의 주머니가 컬럼 단위
- 데이터프레임에 `lapply` 함수를 사용하면 **컬럼단위로 연산** 수행
- `lapply` 함수 수행 결과는 리스트로 반환
```R
> df <- data.frame(a = 1:10, b = 11:20)
> df
      a  b
1   1 11
2   2 12
3   3 13
4   4 14
5   5 15
6   6 16
7   7 17
8   8 18
9   9 19
10 10 20
```
```R
> lapply(df, mean)
$a
[1] 5.5
$b
[1] 15.5
```
```R
> lapply(df, sum)
$a
[1] 55
$b
[1] 155
```

<br>

### 5.2.4 lapply 함수의 단점

- `lapply` 함수의 수행 결과가 리스트로 반환되는 것이 단점이다.

<br>

## 5.3 sapply

- `lapply` 함수와 달리 수행 결과를 **원자 벡터**로 반환하는 함수
```R
> df <- data.frame(a = 1:10, b = 11:20)
> df
      a  b
1   1 11
2   2 12
3   3 13
4   4 14
5   5 15
6   6 16
7   7 17
8   8 18
9   9 19
10 10 20
```
```R
> sapply(df, mean)
    a    b
 5.5 15.5
```
```R
> sapply(df, sum)
   a   b
 55 155
```

<br>

## 5.4 tapply

- 리스트별이나 컬럼별이 아닌 **그룹별**로 동작하는 apply 계열 함수
- `tapply` 함수의 입력 인자 확인
```R
> args(tapply)
function (X, INDEX, FUN = NULL, ..., default = NA, simplify = TRUE)
NULL
```

- `X` : 연산을 수행하고 싶은 데이터 (ex. `iris$Petal.length`)
- `INDEX` : 그룹 정보 (ex. `iris%Species)
- `FUN` : 연산 함수 이름

<br>

### 5.4.1 tapply 함수 사용 예시

- `iris` 데이터
```R
> head(iris)
     Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

<br>

- 꽃잎의 길이 데이터
```R
> head(iris$Petal.Length)
[1] 1.4 1.4 1.3 1.5 1.4 1.7
```

<br>

- 붓꽃 품종의 종류
```R
> head(iris$Species)
[1] setosa setosa setosa setosa setosa setosa
Levels: setosa versicolor virginica
```

<br>

- `iris` 데이터에 `tapply` 함수 사용
```R
> tapply(iris$Petal.Length, iris$Species, mean)
     setosa versicolor  virginica
     1.462      4.260      5.552
```

- `iris` 데이터 중 꽃잎의 길이(`Petal.Length`)의 품종(`Species`)별 평균(`mean`)값 계산
