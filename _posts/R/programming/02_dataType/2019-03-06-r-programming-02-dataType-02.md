---
title: "단일 종류의 데이터"
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

# 2. 단일 종류의 데이터

## 2.1 벡터의 생성: **`c()`**

- 벡터를 만들어주는 함수
- c : combine의 줄임말
- 값들을 결합해서 벡터로 만듬

    ```R
> a <- c(1,2,3)
> a
[1] 1 2 3
    ```

## 2.2 벡터의 정보 확인: `str()`

- str : structure의 줄임말
- 만든 벡터와 같은 데이터 객체의 모양을 확인하는 함수

    ```R
> str(a)
 num [1:3] 1 2 3
    ```

- 해당 함수의 출력값은 Environment 창에서도 확인 가능

## 2.3 벡터의 길이 출력: `length()`
- 길이 : 데이터의 갯수

    ```R
> length(a)
[1] 3
    ```

## 2.4 기본 데이터 종류 확인

### 2.4.1 논리형(logical) 벡터

- 논리형 : 참, 거짓
- R에서는 참은 `T` 또는 `TRUE`, 거짓은 `F` 또는 `FALSE` 로 작성 (전체 대문자)

    ```R
> lgl_v <- c(T, F, TRUE, FALSE)
> lgl_v
[1]  TRUE FALSE  TRUE FALSE
    ```


**`typeof()`**
- 벡터의 종류를 알려주는 함수

    ```R
> typeof(lgl_v)
[1] "logical"
    ```

<br>

### 2.4.2 숫자형 벡터  

<br>

**1) 실수형(double)**  

- double은 실수형을 의미
- R은 실수형을 기본 자료형으로 가짐  


  ```R
  > typeof(1)
  [1] "double"
  ````

<br>

**2) 정수형(integer)**
- integer는 정수형을 의미
- 실수형 데이터에 `L`을 붙여 정수형으로 변환할 수 있다.  

  ```R
> typeof(1L)
[1] "integer"
   ```

<br>

**3) NaN & Inf & NA**
- 숫자형에는 조금 더 특별한 자료형 숫자를 제공한다.

- `sqrt()` : 제곱근 값을 반환하는 함수
- 실수에선 음수의 제곱근을 구할 수 없다.
- `NaN`(Not a Number) : 표현이 불가능한 연산의 답으로 사용    


    ```R
> sqrt(-4)
[1] NaN
    ```


    ```R
> 0/0
[1] NaN
    ```

<br>

- `Inf` : 무한대(Infinite)를 의미
- `NA`(Not Available) : 결측된 값 혹은 사용할 수 없음을 뜻함  


    ```R
> c(10/0, 0/0, NA)
[1] Inf NaN  NA
    ```

<br>

**4) `is.nan()` & `is.na()`**

- 0/0 이 NaN 인지 확인하고 싶다.  


    ```R
> 0/0 == NaN
[1] NA
    ```

- 비교 연산자 == 를 사용하여 확인
- 확인 결과 NA 출력 (같은 지를 확인할 수 없음)
- `is.nan()` 함수를 사용하여 해당 데이터가 NaN이 맞는 지 확인 가능  


    ```R
> is.nan(0/0)
[1] TRUE
    ```

<br>

- NaN은 NA에 포함되어 있다. (NaN $$ \subset $$ NA)
- 그래서 `is.na()` 함수로도 데이터가 NaN인 지 확인할 수 있다.  


    ```R
> is.na(0/0)
[1] TRUE
    ```

- NaN과 NA를 구분하기 쉽지 않기 때문에 NA로만 사용하는 것을 권장한다.

<br>

### 2.4.3 글자형(character) 벡터
- R에서 글자로 인식시켜주기 위해선 따옴표('') 또는 쌍따옴표("")로 감싸줘야 한다.  


    ```R
> chr_v <- c("글자형","a","T","1")
> chr_v
[1] "글자형" "a"      "T"      "1"   
    ```


    ```R
> typeof(chr_v)
[1] "character"
    ```

<br>

- 따옴표를 글자로 인식하려면 쌍따옴표로 감싸주면 된다.  


    ```R
> "따옴표를 글자로 인식하려면 ' 쌍따옴표로 감싼다."
[1] "따옴표를 글자로 인식하려면 ' 쌍따옴표로 감싼다."
    ```

<br>

- 쌍따옴표를 글자로 인식하려면 따옴표로 감싸주면 된다.  


    ```R
> '쌍따옴표를 글자로 인식하려면 " 따옴표로 감싼다.'
[1] "쌍따옴표를 글자로 인식하려면 \" 따옴표로 감싼다."
    ```

<br>

- 같은 것으로 처리하려면 앞에 `\`를 붙여준다.
- `\`는 뒤에 나오는 것이 의미를 가지는 것이 아니라는 것을 알려준다.  


    ```R
> "같은 것으로 처리하고 싶을 때는 \" 같이 표시한다."
[1] "같은 것으로 처리하고 싶을 때는 \" 같이 표시한다."
    ```
