---
title: "리스트 다루기"
date: 2019-03-08
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

# 4. 리스트 다루기

## 4.1 리스트 자료형
- 다양한 종류의 데이터를 가지는 데이터 묶음
- 리스트 자료형 자체도 데이터로 가질 수 있음
- 그래서 **재귀형(recursive)**라고도 표현함  


- 원자 벡터 생성 : `c()` 함수 사용
- 리스트 생성 : `list()` 함수 사용
```R  
> mul_l <- list(1, 2, 3)
> mul_l
[[1]]
[1] 1
[[2]]
[1] 2
[[3]]
[1] 3
```

- 이중 대괄호와 대괄호가 있는 형태

<br>

- str() 함수를 사용하여 어떤 구조인 지 확인  
```R
> str(mul_l)
List of 3
 $ : num 1
 $ : num 2
 $ : num 3
```
- 3개의 요소를 가진 리스트이고, 각각은 숫자(num) 1, 2, 3이다.  

<br>

- 리스트도 데이터에 이름을 지정할 수 있다.  
```R
> mul_ln <- list(a = 1,b = 2,c = 3)
> mul_ln
$a
[1] 1
$b
[1] 2
$c
[1] 3
```

<br>

- 구조 확인  
```R
> str(mul_ln)
List of 3
 $ a: num 1
 $ b: num 2
 $ c: num 3
```
- a 주머니에는 숫자 1 데이터가 있음
- b 주머니에는 숫자 2 데이터가 있음
- c 주머니에는 숫자 3 데이터가 있음

<br>

-  
```R
> mul_ll <- list("a", 1L, 1.5, T, list(1,2))
> mul_ll
[[1]]
[1] "a"
[[2]]
[1] 1
[[3]]
[1] 1.5
[[4]]
[1] TRUE
[[5]]
[[5]][[1]]
[1] 1
[[5]][[2]]
[1] 2
```
```R
> str(mul_ll)
List of 5
 $ : chr "a"
 $ : int 1
 $ : num 1.5
 $ : logi TRUE
 $ :List of 2
  ..$ : num 1
  ..$ : num 2
```
- 5개의 주머니가 있는 리스트가 있음
- 첫 번째 주머니 : character 벡터가 있음
- 두 번째 주머니 : integer 벡터가 있음
- 세 번째 주머니 : number 벡터가 있음
- 네 번째 주머니 : logical 벡터가 있음
- 다섯 번째 주머니 : 리스트가 있음
- 다섯 번째 주머니안에는 또 다른 2개의 주머니가 있다. 각각의 주머니에는 숫자(num) 1과 숫자 2가 있다.
- 리스트 자료형은 실제 데이터를 다룰 땐 많이 사용되지 않지만 지리, 웹 데이터에 자주 사용된다.
- 자유도가 높다.

<br>

## 4.2 리스트 자료형의 데이터 일부 사용하기
- 벡터와 문법이 거의 같음
- 대괄호와 이중 대괄호의 동작 차이가 중요하다.

<br>

### 4.2.1 대괄호 사용  

- 첫 번째 주머니와 두 번째 주머니의 결과를 출력
```R
> mul_ll[c(1,2)]
[[1]]
[1] "a"
[[2]]
[1] 1
```
```R
> str(mul_ll[c(1,2)])
List of 2
 $ : chr "a"
 $ : int 1
```

<br>

- 5번째 주머니 확인
```R
> mul_ll[5]
[[1]]
[[1]][[1]]
[1] 1
[[1]][[2]]
[1] 2
```
```R
List of 1
 $ :List of 2
  ..$ : num 1
  ..$ : num 2
```

<br>

### 4.2.2 이중 대괄호 사용

- 이중 대괄호를 사용하면 벡터를 결과로 출력한다.
- 주머니를 풀어서 안에 있는 데이터를 출력하는 것이다.
```R
> mul_ll[[1]]
[1] "a"
```
```R
> str(mul_ll[[1]])
 chr "a"
```

<br>

- 주머니 2개를 동시에 풀 수는 없다. (벡터에서도 이중 대괄호안에는 1개만 사용 가능)
```R
> mul_ll[[c(1,2)]]
Error in mul_ll[[c(1, 2)]] : subscript out of bounds
```

<br>

- 리스트를 데이터로 가진 주머니 풀기
```R
> mul_ll[[5]]
[[1]]
[1] 1
[[2]]
[1] 2
```
```R
> str(mul_ll[[5]])
List of 2
 $ : num 1
 $ : num 2
```

<br>

### 4.2.3 이름 사용
-  
```R
> mul_ln <- list(a = 1,b = 2,c = 3, d = list(3,4))
> mul_ln[[3]]
[1] 3
```
```R
> mul_ln[["c"]]
[1] 3
```

<br>

- 리스트의 데이터에 이름이 달려있다면 이중 대괄호와 같은 의미인 **$**를 사용할 수 있음
- `[["c"]]` 대신 `$c` 사용
```R
> mul_ln$c
[1] 3
```

<br>

- 리스트의 리스트 가능 $$\rightarrow$$ 이중 대괄호의 대괄호, 이중 대괄호의 이중 대괄호 사용 가능  

<br>

**이중 대괄호의 대괄호**

-  
```R
> mul_ln[["d"]][1]
[[1]]
[1] 3
```

<br>

**이중 대괄호의 이중 대괄호**

-  
```R
> mul_ln[["d"]][[1]]
[1] 3
```
