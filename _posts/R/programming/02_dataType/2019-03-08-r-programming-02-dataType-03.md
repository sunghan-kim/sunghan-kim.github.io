---
title: "단일 종류의 데이터 다루기"
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

# 3. 단일 종류의 데이터 다루기

- 단일 종류의 데이터, 즉 **벡터**를 다룰 땐 몇 가지 이해하고 넘어가야 할 동작들이 있다.

<br>

## 3.1 강제 형변환

- 강제로 다른 종류의 데이터로 바꾸기
- **자료형** : 데이터의 종류
- 벡터는 단일 자료형을 가져야하기 때문에 강제로 형변환을 하게 된다.
- 논리형 $$\rightarrow$$ 숫자형 $$\rightarrow$$ 글자형 순으로 바꿔줌 (정보가 없어지지 않는 순으로 바꿔준다.)  

<div style="text-align: center;">
	<img src="/assets/images/lecture/FE_quant/r/part01/ch02/img002.jpg" width="400px">
</div>

<br>

### 3.1.1 논리형 데이터 $$\rightarrow$$ 숫자형 데이터
```R
> tem <- c(1, T, F, TRUE)
> tem
[1] 1 1 0 1
> typeof(tem)
[1] "double"
```

- 숫자형 데이터와 논리형 데이터를 같이 벡터로 만듬
- 출력결과, TRUE, FALSE가 아닌 숫자인 것 확인
- 자료형 또한 double이다.
- 이는 논리형 데이터를 숫자형으로 바꿔줬다는 것을 의미한다.
- TRUE는 1, FALSE는 0으로 변환된 것 확인

<br>

### 3.1.2 숫자형 데이터 $$\rightarrow$$ 글자형 데이터
```R
> typeof(tem)
[1] "double"
> tem <- c("글자", 1, -1)
> tem
[1] "글자" "1"    "-1"  
> typeof(tem)
[1] "character"
```

- 글자형 데이터와 숫자형 데이터를 같이 벡터로 만듬
- 출력결과, 쌍따옴표로 감싸져 있는 것을 통해 문자형으로 변환된 것 확인
- 자료형이 character 인 것을 통해서도 형변환 된 것 확인

<br>

### 3.1.3 논리형 데이터 $$\rightarrow$$ 글자형 데이터
```R
> tem <- c("글자", T, FALSE)
> tem
[1] "글자"  "TRUE"  "FALSE"
> typeof(tem)
[1] "character"
```

- 논리형 데이터와 글자형 데이터를 같이 벡터로 만듬
- 출력결과, 모두 글자형으로 형변환된 것 확인
- 주의할 점 : 논리형 데이터 **T**는 글자형으로 형변환 되면서 값이 **TRUE**로 바뀜

<br>

## 3.2 강제로 데이터의 길이 맞추기
- 스칼라 : 1개의 데이터
- 벡터 : 1개 이상의 데이터
- 벡터는 스칼라를 포함 (스칼라 $$\subset$$ 벡터)

<br>

### 3.2.1 스칼라와 벡터 사이의 연산
- 데이터가 여러 개인 데이터와 하나인 데이터를 연산
```R
> 1:10
 [1]  1  2  3  4  5  6  7  8  9 10
> 1:10 + 10
 [1] 11 12 13 14 15 16 17 18 19 20
```

- `1:10` = 1부터 10까지의 정수 벡터
- 연산 결과 벡터의 모든 데이터들에 대해 하나의 데이터가 더해진다.

<br>

### 3.2.2 길이가 다른 벡터 사이의 연산 (재활용 규칙)
- 1부터 10까지 길이 10개의 데이터와 1부터 5까지 길이 5개의 데이터를 더함
```R
> 1:10 + 1:5
 [1]  2  4  6  8 10  7  9 11 13 15
```
- 길이가 짧은 벡터가 재활용되어 연산이 수행됨
- 이 부분을 R에서는 **재사용 규칙**이라고 함   


- 두 벡터의 사이즈가 맞아야 재사용 규칙이 적용된다.
```R
> 1:10 + 1:3
 [1]  2  4  6  5  7  9  8 10 12 11
Warning message:
In 1:10 + 1:3 :
  longer object length is not a multiple of shorter object length
```
- 재사용이 가능한 만큼 연산이 수행되고 경고 메세지가 출력된다.

<br>

## 3.3 벡터내의 데이터에 이름 지정
- 벡터내의 데이터에 이름을 지정할 수 있음
- 이것을 **key-value** 라고 부른다. (**key**=이름, **value**=데이터)
- 형식 : `key = value`
- key는 이름이기 때문에 따옴표를 생략할 수 있다.  
```R
> c("a" = "k")
  a
"k"
```
```R
> c(a = "k", b = "kk", c = "kkk")
    a     b     c
  "k"  "kk" "kkk"
```

<br>

## 3.4 서브셋(subset)
- 데이터의 일부를 사용
- 형식 : `벡터[]`
- 대괄호 안에 벡터를 넣어서 일부의 데이터를 사용한다.

<br>

### 3.4.1 논리형 벡터 이용 데이터 일부 사용
- 벡터 생성
```R
> subs <- c("하나", "둘", "셋", "넷", "다섯")
```
- 대괄호안에 아무것도 넣지 않으면 전체가 출력된다.
```R
> subs[]
[1] "하나" "둘"   "셋"   "넷"   "다섯"
```
- 대괄호 안에 subs 벡터와 같은 길이의 T, F 데이터를 가진 벡터를 넣으면 TRUE에 해당하는 인덱스의 데이터만 출력된다.
```R
> subs[c(T,F,T,F,T)]
[1] "하나" "셋"   "다섯"
```
- 대괄호안의 벡터에 대해 재사용 규칙이 적용된다.
```R
> subs[c(T,F)] # 재사용 규칙 활용 (T F T F T F)
[1] "하나" "셋"   "다섯"
```
- 대괄호 안의 벡터의 길이가 더 길면 긴 만큼의 출력은 NA가 된다.
```R
> subs[c(T,F,T,F,T,T,T)]
[1] "하나" "셋"   "다섯" NA     NA
```

<br>

### 3.4.2 숫자형 벡터 이용 데이터 일부 사용

- 숫자형으로 가져오는 걸 **인덱싱(indexing)** 이라고 한다.
- 데이터의 위치를 1, 2, 3, ... 이라고 지정
```R
> subs[c(1,2,3)]
[1] "하나" "둘"   "셋"
```
- 위치를 지정
```R
> subs[c(3,2,1)]
[1] "셋"   "둘"   "하나"
```
- 반복 사용
```R
> subs[c(1,1,1,1,1)]
[1] "하나" "하나" "하나" "하나" "하나"
```
- 음수 사용 : 그 위치를 제외한 나머지를 사용
```R
> subs[c(-1,-2)]
[1] "셋"   "넷"   "다섯"
```
- 양수와 음수 동시에 사용 불가
```R
> subs[c(-1,1)]
Error in subs[c(-1, 1)] : only 0's may be mixed with negative subscripts
```
- 원래 데이터의 범위를 벗어나면 NA 출력
```R
> subs[c(6)]
[1] NA
```

<br>

### 3.4.3 글자형 벡터 이용 데이터 일부 사용
- 글자형 벡터로 일부를 사용하려면 데이터에 이름을 지정해두어야 한다.
```R
> subs_name <- c(a = "하나", b = "둘", c = "셋", d = "넷", e = "다섯")
```
- 숫자형과 같이 위치를 지정할 수 있고, 해당 이름을 가진 데이터가 없으면 NA를 출력한다.
```R
> subs_name[c("a","c","f", "a")]
     a      c   <NA>      a
"하나"   "셋"     NA "하나"
```
- 글자형에선 `-`를 사용할 수 없음
```R
> subs_name[c(-"a")]
Error in -"a" : invalid argument to unary operator
```

<br>

### 3.4.4 이중 대괄호 사용
- 이름 한 가지만 지정해서 가져올 수 있음
- 이중 대괄호를 사용하면 이름 없이 데이터만 가져오는 것 확인
```R
> subs_name[["a"]]
[1] "하나"
```
```R
> subs_name[[c("a","b")]]
Error in subs_name[[c("a", "b")]] :
  attempt to select more than one element in vectorIndex
```
```R
> subs_name[[1]]
[1] "하나"
```
