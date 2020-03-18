---
title: "확장 벡터 (데이터프레임)"
date: 2019-03-10
category:
  - R
tag :
  - 데이터프레임(data.frame)
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

### 5.2.3 데이터프레임(data.frame)

- 가장 많이 사용
- 2차원 테이블 형태의 자료구조
- 데이터프레임은 리스트의 확장
- 리스트보다 엄격한 조건을 갖춰야 함
- 리스트 같이 주머니별로 데이터의 종류가 다를 수 있음
- 리스트에서의 주머니를 데이터프레임에서는 **컬럼**이라고 함
- 컬럼별로 다양한 종류의 데이터를 가질 수 있다.  

<br>

**1) 데이터프레임 생성**

- 3가지 자료형의 벡터 만들기
```R
> lgl <- c(T,F,T,T) # 논리형
> chr <- c("영수", "영미", "철수", "철이") # 글자형
> num <- c(15,14,16,13) # 숫자형
```

- `data.frame()` 함수 이용 데이터프레임 생성
- 해당 함수 안에 `이름=데이터` 방식으로 지정

-
```R
> school <- data.frame(이름 = chr, 성별 = lgl, 나이 = num)
```

- 데이터프레임에선 **이름**이 굉장히 중요 (이름이 컬럼 이름이기 때문)
- 행 이름은 관례적으로 row number 사용
- 지정한 컬럼의 이름은 리스트의 주머니의 이름이다.
```R
> school
    이름  성별 나이
1 영수  TRUE   15
2 영미 FALSE   14
3 철수  TRUE   16
4 철이  TRUE   13
```


- 생성한 데이터프레임의 구조 확인
```R
'data.frame':	4 obs. of  3 variables:
 $ 이름: Factor w/ 4 levels "영미","영수",..: 2 1 3 4
 $ 성별: logi  TRUE FALSE TRUE TRUE
 $ 나이: num  15 14 16 13
```

- `4 obs` : 관측치가 4개이다. (행이 4개)
- `3 variables` : 컬럼이 3개이다.  

<br>

- `$ 이름: Factor` : 이름 컬럼을 글자형(character)을 이용하여 만들었지만 Factor 자료형이 되어 있다.
```R
> args(data.frame)
function (..., row.names = NULL, check.rows = FALSE, check.names = TRUE,
    fix.empty.names = TRUE, stringsAsFactors = default.stringsAsFactors())
NULL
```

- `data.frame()` 함수의 `stringsAsFactors` 옵션이 `default.stringsAsFactors()`로 되어 있기 때문
```R
> default.stringsAsFactors()
[1] TRUE
```

- `stringsAsFactors=TRUE`이기 때문에 strings(R에선 character와 같음)이 factor로 바뀐다.

<br>

- `stringsAsFactors=FALSE`로 지정하여 데이터프레임 생성
```R
> school <- data.frame(이름 = chr, 성별 = lgl, 나이 = num, stringsAsFactors = F)
> str(school)
'data.frame':	4 obs. of  3 variables:
 $ 이름: chr  "영수" "영미" "철수" "철이"
 $ 성별: logi  TRUE FALSE TRUE TRUE
 $ 나이: num  15 14 16 13
```

- 이름 컬럼의 자료형이 `chr`로 바뀐 것 확인

<br>

**2) 데이터프레임 구조 확인 (type, attribute, dim, length)**

- 데이터프레임의 type
```R
> typeof(school)
[1] "list"
```

<br>

- 데이터프레임의 속성(attribute)
```R
> attributes(school)
$names
[1] "이름" "성별" "나이"
$class
[1] "data.frame"
$row.names
[1] 1 2 3 4
```

- 데이터프레임의 속성값 확인을 위한 함수(`names()`, `class()`, `row.names()`) 제공
```R
> names(school)
[1] "이름" "성별" "나이"
> class(school)
[1] "data.frame"
> row.names(school)
[1] "1" "2" "3" "4"
```

<br>

- 데이터프레임의 차원 확인 (`dim()` 함수 이용)
```R
> dim(school) # 행갯수 열갯수
[1] 4 3
```

<br>

- `length()` : 리스트의 개념을 적용한 데이터프레임의 길이(컬럼(주머니) 갯수)
```R
> length(school)
[1] 3
```

<br>

**3) 데이터프레임과 리스트의 차이점**

- 데이터프레임은 행과 열을 이루는 2차원 데이터이기 때문에 메트릭스의 동작을 같이 수행할 수 있다.
- 그래서 주머니내의 데이터 길이가 같아야 한다.

<br>

- 서로 다른 길이를 갖는 벡터를 이용하여 데이터프레임 생성
```R
> lgl <- c(T,F,T,T)
> chr <- c("영수", "영미", "철수", "철이")
> num <- c(15,14,16,13, 18)
> school2 <- data.frame(이름 = chr, 성별 = lgl, 나이 = num)
Error in data.frame(이름 = chr, 성별 = lgl, 나이 = num) :
  arguments imply differing number of rows: 4, 5
```

- `num` 벡터의 길이가 다른 벡터들의 길이와 같지 않기 때문에 에러 발생

<br>

- 메트릭스에서 사용하는 것과 같은 `cbind()`, `rbind()` 함수 제공

<br>

- `cbind()`
```R
> 몸무게 <- c(35, 38, 40, 25)
> cbind(school, 몸무게)
    이름  성별 나이 몸무게
1 영수  TRUE   15     35
2 영미 FALSE   14     38
3 철수  TRUE   16     40
4 철이  TRUE   13     25
```

- 벡터의 길이가 맞지 않으면 `cbind()` 함수 사용 시 에러 발생
```R
> 몸무게 <- c(35, 38, 40)
> cbind(school, 몸무게)
Error in data.frame(..., check.names = FALSE) :
  arguments imply differing number of rows: 4, 3
```

<br>

- `rbind()`
- 데이터프레임의 행단위 데이터 추가
- 컬럼의 순서는 중요하지 않음 (컬럼 이름으로 어느 데이터를 합쳐야 하는 지 알려주기 때문)
```R
> 전학생 <- data.frame(성별 = F, 이름 = "영희", 나이 = 18)
> rbind(school, 전학생)
  이름  성별 나이
1 영수  TRUE   15
2 영미 FALSE   14
3 철수  TRUE   16
4 철이  TRUE   13
5 영희 FALSE   18
```

<br>

**4) 메트릭스와 데이터프레임 사이의 변환**

**(1) 데이터프레임 $$\rightarrow$$ 메트릭스**

- 데이터프레임을 메트릭스로 강제 형변환
```R
> as.matrix(school)
     이름   성별    나이
[1,] "영수" " TRUE" "15"
[2,] "영미" "FALSE" "14"
[3,] "철수" " TRUE" "16"
[4,] "철이" " TRUE" "13"
```
- 모든 데이터의 자료형이 글자형으로 바뀜(메트릭스의 특성)

<br>

**(2) 메트릭스 $$\rightarrow$$ 데이터프레임**

- 메트릭스를 데이터프레임으로 강제 형변환
```R
> mtrx <- matrix(1:10, nrow = 5)
> mtrx
     [,1] [,2]
[1,]    1    6
[2,]    2    7
[3,]    3    8
[4,]    4    9
[5,]    5   10
> as.data.frame(mtrx)
  V1 V2
1  1  6
2  2  7
3  3  8
4  4  9
5  5 10
```

- 임의의 컬럼 이름 강제 지정

<br>

**5) 데이터프레임의 일부 데이터 사용**

- 리스트와 마찬가지로 데이터프레임의 일부 데이터 사용 가능
```R
> school[,1]
[1] "영수" "영미" "철수" "철이"
```
```R
> school[,c(1,2)]
  이름  성별
1 영수  TRUE
2 영미 FALSE
3 철수  TRUE
4 철이  TRUE
```
```R
> school[,-1]
   성별 나이
1  TRUE   15
2 FALSE   14
3  TRUE   16
4  TRUE   13
```
```R
> school[,c("성별","이름")]
   성별 이름
1  TRUE 영수
2 FALSE 영미
3  TRUE 철수
4  TRUE 철이
```

- 이중 대괄호 사용도 가능
```R
> school[["이름"]] # 컬럼의 이름이 "이름"인 컬럼 데이터 확인
[1] "영수" "영미" "철수" "철이"
```

- `$`를 사용하여 특정 컬럼의 데이터 확인
```R
> school$이름
[1] "영수" "영미" "철수" "철이"
```

<br>

**6) 데이터프레임 데이터 추가 및 삭제**

**(1) 데이터 추가**

- 화살표(`<-`)를 이용하여 데이터프레임에 새로운 컬럼 추가
```R
> school$몸무게 <- c(35, 38, 40, 25)
> school
  이름  성별 나이 몸무게
1 영수  TRUE   15     35
2 영미 FALSE   14     38
3 철수  TRUE   16     40
4 철이  TRUE   13     25
```

<br>

**(2) 데이터 삭제**

- 컬럼에 `NULL`을 지정하여 해당 컬럼 삭제
```R
> school$몸무게 <- NULL
> school
  이름  성별 나이
1 영수  TRUE   15
2 영미 FALSE   14
3 철수  TRUE   16
4 철이  TRUE   13
```
