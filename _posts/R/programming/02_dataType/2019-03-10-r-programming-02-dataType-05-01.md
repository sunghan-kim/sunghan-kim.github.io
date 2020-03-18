---
title: "데이터에 속성 추가"
date: 2019-03-10
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

# 5. 속성을 가지는 확장 벡터

<br>

## 5.1 데이터에 속성 추가

- 확장 벡터는 속성을 가짐
- 속성(attribute) : 메타 데이터, "데이터의 데이터"
- 저장하는 데이터에 대해서 그 데이터 그 자체에 대한 데이터
- `attr()` 함수를 사용  

<br>

- 1부터 10까지의 데이터 생성
```R
> x <- 1:10
> x
 [1]  1  2  3  4  5  6  7  8  9 10
```

<br>

- x 벡터에 "test" 라는 메타 데이터가 있는 지 확인
```R
> attr(x, "test")
NULL
```

<br>

- x 벡터에 "test" 라는 메타 데이터가 "ok!" 라는 것을 지정
```R
attr(x, "test") <- "ok!"
```

- x 벡터에 "done" 라는 메타 데이터가 "not yet!" 라는 것을 지정
```R
> attr(x, "done") <- "not yet!"
```

<br>

- `attributes()` 함수를 사용하여 x 벡터의 전체 메타 데이터(속성) 확인
```R
> attributes(x)
$test
[1] "ok!"
$done
[1] "not yet!"
```

<br>

- 다시 한번 x 벡터에 "test" 라는 메타 데이터가 있는 지 확인
```R
> attr(x, "test")
[1] "ok!"
```

<br>

- R에는 벡터들이 기본적으로 가지는 속성(메타 데이터)들이 있다.
- 가장 많이 사용하는 속성으로는 **names**와 **class**가 있다.

<br>

### 5.1.1 names 속성

- 리스트 생성
```R
> mul_ln <- list(a = 1,b = 2,c = 3, d = list(3,4))
```

<br>

- 리스트의 속성 확인
```R
> attributes(mul_ln)
$names
[1] "a" "b" "c" "d"
```
- 각 주머니에 대한 names라는 속성을 가지고 있다.

<br>

- 리스트의 names 속성의 값 확인
```R
> attributes(mul_ln)$names
[1] "a" "b" "c" "d"
```

- 위 코드를 함수로 제공해주고 있음
- names 속성을 확인하는 함수 `names()`를 사용하여 names 속성값 확인
```R
> names(mul_ln)
[1] "a" "b" "c" "d"
```

<br>

### 5.1.2 class 속성

- 데이터 프레임 생성
```R
> df_ln <- data.frame(a = 1,b = 2,c = 3)
```

<br>

- 데이터 프레임의 속성 확인
```R
> attributes(df_ln)
$names
[1] "a" "b" "c"
$class
[1] "data.frame"
$row.names
[1] 1
```

<br>

- 데이터 프레임의 class 속성값 확인 (`class()` 함수 이용)
```R
> class(df_ln)
[1] "data.frame"
```
