---
title: "반복문 for"
date: 2019-03-13
category:
  - R
tag :
  - for문
  - 반복문
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

# 3. 반복문 for

## 3.1 반복문 기본

- 반복문의 기본 문법
```R
for (내부에서 사용할 지역 변수 in 전체 사용할 벡터) {
	print(내부에서 사용할 지역 변수)
}
```

<br>

- 반복문 예시 (1)
```R
> for (i in 1:10) {
	print(i)
 }
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
[1] 6
[1] 7
[1] 8
[1] 9
[1] 10
```

<br>

- 반복문 예시 (2)
```R
> for (i in 10:1) {
	print(i)
 }
[1] 10
[1] 9
[1] 8
[1] 7
[1] 6
[1] 5
[1] 4
[1] 3
[1] 2
[1] 1
```

<br>

- 반복문 예시 (3) : 글자형 벡터 반복
```R
> chr_v <- c("a","b","c","d","e","f")
```
```R
> for (i in chr_v) {
	print(i)
 }
[1] "a"
[1] "b"
[1] "c"
[1] "d"
[1] "e"
[1] "f"
```

<br>

## 3.2 next

- `next` : 다음 반복으로 넘어가라는 뜻
```R
> for (i in 1:10) {
	if (i == 4) {
		next
	}
	print(i)
 }
[1] 1
[1] 2
[1] 3
[1] 5
[1] 6
[1] 7
[1] 8
[1] 9
[1] 10
```

- `i=4` 일 때는 출력되지 않는 것 확인

<br>

## 3.3 break

- `break` : 반복문을 종료하라는 뜻
```R
> for (i in 1:10) {
	if (i == 4) {
		break
	}
	print(i)
 }
[1] 1
[1] 2
[1] 3
```

- 3까지만 출력된 것 확인
