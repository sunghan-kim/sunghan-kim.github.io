---
title: "R의 기본 연산자"
date: 2019-03-10
category:
  - R
tag :
  - R 연산자
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

# 6. R의 기본 연산자

<br>

## 6.1 연산자

- 프로그램의 계산을 총칭
- 연산자의 종류 : 할당, 산술, 관계, 논리

<br>

### 6.1.1 할당 연산자

- "assign" 이라는 단어를 번역한 것
- "선언하다", "할당하다" 등의 단어로 표현
- R은 다른 언어와 달리 할당 연산자로서 `<-` 를 사용
```R
> a <- c("a","b","c")
> a
[1] "a" "b" "c"
```

- 다른 언어들 처럼 할당 연산자로 `=`를 사용할 수 있지만 권장하지 않음
```R
> b = c("a","b","c")
> b
[1] "a" "b" "c"
```

<br>

- 할당 연산자는 기본적으로 오른쪽에 있는 내용을 왼쪽에 할당함
- 할당 연산자 `<-` 는 방향을 바꿔 `->`로도 사용 가능
- 이렇게 되면 왼쪽에 있는 내용을 오른쪽에 할당하게 된다.
```R
> c("a","b","c") -> d
> d
[1] "a" "b" "c"
```

<br>

### 6.1.2 산술 연산자

- 계산을 수행하는 연산자
```R
> 1 + 1   # 더하기
[1] 2
```
```R
> 2 - 1   # 빼기
[1] 1
```
```R
> 1 * 2   # 곱하기
[1] 2
```
```R
> 4 / 2   # 나누기
[1] 2
```
```R
> 2^4     # 거듭제곱(지수)
[1] 16
```
```R
> 5 %% 2  # 나누기의 나머지
[1] 1
```
```R
> 5 %/% 2 # 나누기의 몫
[1] 2
```

<br>

### 6.1.3 관계 연산자

- 왼쪽과 오른쪽의 상태를 비교
```R
> 4 == 5 # 같다
[1] FALSE
```
```R
> 4 != 5 # 같다가 아니다 = 다르다, 원래 표현 : !(4 == 5)
[1] TRUE
```
```R
> 4 > 5 # 왼쪽이 크다
[1] FALSE
```
```R
> 4 < 5 # 오른쪽이 크다
[1] TRUE
```
```R
> 4 >= 5 # 왼쪽이 크거나 같다
[1] FALSE
```
```R
> 4 <= 5 # 오른쪽이 크거나 같다
[1] TRUE
```

- `==`와 `=`는 다르다는 것 주의 (`=`는 할당 연산자)
- `<=`와 `<-`도 다르다는 것 주의

<br>

### 6.1.4 논리 연산자

- 논리형 벡터에 대해 더하거나 곱하는 연산을 수행

<br>

**1) 논리곱(AND)**

-    
```R
> c(T,T,F) & T   # 논리곱
[1]  TRUE  TRUE FALSE
```
```R
> c(T,T,F) && T  # 논리곱의 첫번째 결과(T & T)만 출력
[1] TRUE
```

<br>

**2) 논리합(OR)**

-     
```R
> c(T,T,F) | T   # 논리합
[1] TRUE TRUE TRUE
```
```R
> c(F,T,F) || F  # 논리합의 첫번째 결과(F | F)만 출력
[1] FALSE
```

<br>

**3) 논리부정(NOT)**

-    
```R
> !F   # 논리부정(반대)
[1] TRUE
```
```R
> !T
[1] FALSE
```

<br>

**4) `all()` 함수**

- 벡터 안의 모든 데이터가 TRUE이어야 TRUE 반환
- 데이터 중 하나라도 FALSE이면 FALSE 반환
```R
> all(c(T,T,T,T,T,T))
[1] TRUE
```
```R
> all(c(T,T,T,T,T,F))
[1] FALSE
```
```R
> all(c(F,F,F,F,F,F))
[1] FALSE
```

<br>

**5) `any()` 함수**

- 벡터 안의 데이터 중 하나라도 TRUE가 포함되면 TRUE 반환
- 벡터 안의 모든 데이터가 FALSE이어야 FALSE 반환
```R
> any(c(T,T,T,T,T,T))
[1] TRUE
```
```R
> any(c(T,T,T,T,T,F))
[1] TRUE
```
```R
> any(c(T,F,F,F,F,F))
[1] TRUE
```
```R
> any(c(F,F,F,F,F,F))
[1] FALSE
```
