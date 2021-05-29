---
title: "확장 벡터 (요인형)"
date: 2019-03-10
category:
  - R
tag :
  - 요인형(Factor)
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

### 5.2.1 요인형(factor)

- 독특한 동작을 제공
- R에만 있는 자료형
- 요인형 데이터는 `factor()` 함수를 사용해 만들 수 있음

<br>

**1) levels의 갯수와 동일한 갯수의 데이터를 가지는 요인형 벡터**
-  Levels의 갯수 = 데이터의 갯수
```R
> fct <- factor(c("a","b","c"))
> fct
[1] a b c
Levels: a b c
```

- a, b, c 데이터가 있고, Levels 라는 것이 있음

<br>

- 요인형의 type 확인
```R
> typeof(fct)
[1] "integer"
```

- 요인형의 속성 확인
```R
> attributes(fct)
$levels
[1] "a" "b" "c"
$class
[1] "factor"
```

- 요인형의 속성으론 levels와 class가 있음

<br>

- 요인형의 구조 확인
```R
> str(fct)
 Factor w/ 3 levels "a","b","c": 1 2 3
```

- "a", "b", "c" 라는 levels을 가지고 있는 1, 2, 3 이라는 데이터이다.
- levels은 이름과 같은 효과를 준다.
- 1, 2, 3 은 데이터 그 자체를 의미한다.

<br>

**2) levels의 갯수보다 많은 데이터를 가지는 요인형 벡터**
-  Levels의 갯수 < 데이터의 갯수
```R
> fct <- factor(c("a","b","c","a","a"))
> fct
[1] a b c a a
Levels: a b c
```

- Levels는 "a", "b", "c" 를 유지하면서 데이터만 추가

<br>

- 구조 확인
```R
> str(fct)
 Factor w/ 3 levels "a","b","c": 1 2 3 1 1
```

- "a", "b", "c" 라는 이름이 있는 데이터가 있음
- 첫 번째 데이터는 1, 즉 "a"에 해당
- 두 번째 데이터는 2, 즉 "b"에 해당
- 세 번째 데이터는 3, 즉 "c"에 해당
- 네 번째 데이터는 1, 즉 "a"에 해당
- 다섯 번째 데이터는 1, 즉 "a"에 해당

<br>

- `levels()` 함수를 이용하여 요인형의 levels 확인
```R
> levels(fct)
[1] "a" "b" "c"
```

<br>

**3) 요인형 데이터의 예**
- 혈액형 (levels: A, B, AB, O)
- 옷의 사이즈
- 학교의 반  

<br>

- R은 회귀 분석 등에서 요인형을 유용하게 사용한다.
- 예를 들어, 요인형을 사용하게 되면 따로 더미변수를 만들지 않아도 된다.

<br>

**4) 요인형 강제 형변환**

- 요인형의 type : integer
```R
> typeof(fct)
[1] "integer"
```

<br>

- `as.numeric()` 함수를 이용하여 숫자형으로 강제 형변환
```R
> as.numeric(fct)
[1] 1 2 3 1 1
> typeof(as.numeric(fct))
[1] "double"
```

<br>

- `as.character()` 함수를 이용하여 글자형으로 강제 형변환
```R
> as.character(fct)
[1] "a" "b" "c" "a" "a"
> typeof(as.character(fct))
[1] "character"
```

<br>

- 숫자형 데이터를 갖는 요인형 벡터
```R
> fct_m <- factor(c(4,8,3))
> fct_m
[1] 4 8 3
Levels: 3 4 8
```

<br>

- `as.numeric()` 함수를 이용하여 숫자형으로 강제 형변환
```R
> as.numeric(fct_m)
[1] 2 3 1
```

<br>

- 이 요인형 벡터는 "3", "4", "8" 이라는 Levels 를 갖는 2, 3, 1 정수형 데이터이다.
```R
> str(fct_m)
 Factor w/ 3 levels "3","4","8": 2 3 1
```

- Levels 의 "3", "4", "8' 은 쌍따옴표로 감싸진걸로 보아 글자형인 걸 알 수 있다.

<br>

- `as.character()` 함수를 이용하여 형변환
```R
> as.character(fct_m)
[1] "4" "8" "3"
```

- Levels 확인
```R
> levels(fct_m)
[1] "3" "4" "8"
```
