---
title: "반복문 작성 예시"
date: 2019-03-13
category:
  - R
tag :
  - 반복문 작성 예시
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

# 4. 반복문 작성 예시

## 4.1 데이터프레임과 함께 사용

- 데이터프레임에 데이터를 추가, 수정하거나 생성되는 데이터를 데이터프레임에 저장할 때 반복문 사용

<br>

### 4.1.1 데이터프레임의 데이터 출력

- 반복문을 이용하여 데이터프레임의 데이터 출력

<br>

**1) 데이터프레임 정의**

- 아래와 같은 데이터프레임을 정의한다.
```R
> df <- data.frame(a = c("a","b","c","d","e","f"), b = 1:6, stringsAsFactors = F)
> df
    a b
1 a 1
2 b 2
3 c 3
4 d 4
5 e 5
6 f 6
```

<br>

**2) nrow() 함수**

- `nrow()` : 행의 개수를 반환하는 함수
```R
> nrow(df)
[1] 6
```

<br>

**3) 반복문을 이용하여 데이터프레임의 데이터 출력**

- 데이터프레임의 행의 개수만큼 반복문을 반복하여 데이터프레임의 데이터를 출력한다.

<br>

- "a" 컬럼에 해당하는 데이터만 출력
```R
> for (i in 1:nrow(df)) {
	print(df[i,"a"])
 }
[1] "a"
[1] "b"
[1] "c"
[1] "d"
[1] "e"
[1] "f"
```

<br>

- "b" 컬럼에 해당하는 데이터만 출력
```R
> for (i in 1:nrow(df)) {
	print(df[i,"b"])
 }
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
[1] 6
```

<br>

### 4.1.2 데이터프레임에 데이터 추가

- 반복문을 이용하여 데이터프레임에 데이터를 추가한다.

<br>

**1) 데이터프레임 정의**

- 데이터를 추가할 데이터프레임을 정의
```R
> df <- data.frame(a = c("a","b","c"), b = 1:3, stringsAsFactors = F)
> df
    a b
1 a 1
2 b 2
3 c 3
```

<br>

**2) 데이터프레임에 추가할 데이터 정의**

- 각각 "a", "b" 열에 추가할 데이터 정의
```R
> add_a <- c("d","e","f","g")
> add_a
[1] "d" "e" "f" "g"
```
```R
> add_b <- 4:7
> add_b
[1] 4 5 6 7
```

<br>

**3) 데이터 추가**

- 반복문을 이용하여 데이터 추가
```R
> for (i in 1:length(add_a)) {
	print("for start")
	# 각각 add_a, add_b에서 각각 데이터를 하나씩 가져와 임시 데이터프레임 생성
	tem <- data.frame(a = add_a[i], b = add_b[i], stringsAsFactors = F)
	# 임시로 생성한 데이터프레임을 df 데이터프레임과 rbind() 함수를 이용하여 결합
	# 데이터를 추가하는 효과를 볼 수 있음
	df <- rbind(df, tem)
	# 데이터가 추가될 때마다 데이터프레임 확인
	print(df)
 }
[1] "for start"
  a b
1 a 1
2 b 2
3 c 3
4 d 4
[1] "for start"
  a b
1 a 1
2 b 2
3 c 3
4 d 4
5 e 5
[1] "for start"
  a b
1 a 1
2 b 2
3 c 3
4 d 4
5 e 5
6 f 6
[1] "for start"
  a b
1 a 1
2 b 2
3 c 3
4 d 4
5 e 5
6 f 6
7 g 7
```

- 데이터가 추가된 데이터프레임 확인
```R
> df
    a b
1 a 1
2 b 2
3 c 3
4 d 4
5 e 5
6 f 6
7 g 7
```

<br>

### 4.1.3 데이터프레임을 파일로 저장

- `paste0()` : 글자들을 모아 하나의 글자로 만들어주는 함수
```R
> paste0("a", "b")
[1] "ab"
```

- `paste0()` 함수를 이용하여 파일명 생성

<br>

**1) 데이터프레임 생성**

- csv파일로 저장할 대상 데이터프레임 생성
```R
> df <- data.frame(a = c("a","b","c","d","e","f"), b = 1:6, stringsAsFactors = F)
> df
    a b
1 a 1
2 b 2
3 c 3
4 d 4
5 e 5
6 f 6
```

<br>

**2) 파일 저장**

- 반복문을 이용하여 데이터프레임의 데이터를 행별로 csv파일로 저장
- "a" 컬럼의 값을 파일명으로 지정하여 저장
- 반복시마다 "a" 컬럼의 값과 ".csv" 문자를 `paste0()` 함수를 이용하여 결합
- 결합한 문자를 파일명으로 하여 `write.csv()` 함수를 이용 파일 저장
```R
> for (i in 1:nrow(df)) {
	# 파일명 생성
    file_name <- paste0(df[i,"a"],".csv")
	print(file_name)
	# 파일 저장
    write.csv(df[i, ], file_name)
 }
[1] "a.csv"
[1] "b.csv"
[1] "c.csv"
[1] "d.csv"
[1] "e.csv"
[1] "f.csv"
```

<br>

**3) 결과 확인**

- a.csv : 데이터프레임의 첫 번째 행 데이터가 들어있음
```
"","a","b"
"1","a",1
```

- f.csv : 데이터프레임의 마지막 행 데이터가 들어있음
```
"","a","b"
"6","f",6
```

<br>

**cf) 반복문 사용 파일 저장의 잘못된 예**

- 반복문 실행 시 반복시마다 파일명을 만들어주지 않으면 가장 마지막 반복문 내용이 파일로 저장됨
```R
> for (i in 1:nrow(df)) {
	print(i)
	write.csv(df[i, ], "file_name.csv")
 }
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
[1] 6
```

- 저장된 파일 확인
```
"","a","b"
"6","f",6
```
