---
title: "에러 처리"
date: 2019-03-14
category:
  - R
tag :
  - try() 함수
  - tryCatch() 함수
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

#  6. 에러 처리

## 6.1 for문 사용 시 에러 처리

- for문을 실행할 때 에러가 발생하면 for문이 멈춤

<br>

**try() 함수**
- 에러가 발생해도 에러가 발생했다는 것을 알려준 뒤 for문을 멈추지 않고 계속 실행시켜줌
- 크롤링할 때 유용하게 사용

<br>

### 6.1.1 try() 함수의 사용

- **데이터 생성**
```R
> dat <- data.frame(a = 5, b = c(1,2,3,4))
> dat
  a b
1 5 1
2 5 2
3 5 3
4 5 4
```

<br>

- **for문 실행**
```R
> for (i in 1:4) {
	if (i == 3) {
		print(kt)
	}
	print(dat$a[i] / dat$b[i])
 }
[1] 5
[1] 2.5
Error in print(kt) : object 'kt' not found
```

- `i==3` 일 때 `kt`를 출력하는데 `kt`가 정의되어 있지 않아 에러발생
- 에러발생한 시점에서 for문은 실행을 멈춤

<br>

- **`try()` 함수 사용 for문 실행**
```R
> for (i in 1:4) {
	if (i == 3) {
		try(print(kt))
	}
	print(dat$a[i] / dat$b[i])
 }
[1] 5
[1] 2.5
Error in print(kt) : object 'kt' not found
[1] 1.666667
[1] 1.25
```

- 에러가 발생할 것으로 예상되는 부분은 `try()` 함수로 감싸줌
- for문 실행 시 에러가 발생하면 에러 발생을 알려준 뒤 for문을 계속해서 실행

<br>

- **에러 발생 여부 출력 안하기**
```R
> for (i in 1:4) {
	if (i == 3) {
		try(print(kt), silent = T)
	}
	print(dat$a[i]/dat$b[i])
 }
[1] 5
[1] 2.5
[1] 1.666667
[1] 1.25
```

- `try()` 함수의 `silent=T` 옵션을 사용하여 에러를 출력 안함
- 발생할 수 있다는 에러에 대해 출력을 없앨 수 있음 (ex. 데이터 길이가 안맞을 수 있을 때)

<br>

- **발생한 에러를 저장하여 확인**
```R
> for (i in 1:4) {
	if (i == 3) {
		err <- try(print(kt), silent = T)
	}
	print(dat$a[i]/dat$b[i])
 }
[1] 5
[1] 2.5
[1] 1.666667
[1] 1.25
```
```R
> err
# [1] "Error in print(kt) : object 'kt' not found\n"
# attr(,"class")
# [1] "try-error"
# attr(,"condition")
# <simpleError in print(kt): object 'kt' not found>
```

- 에러정보를 저장한 `err`에서 `try-error` 클래스의 에러가 발생했다는 것을 확인
- 다음과 같이 `try-error` 클래스에 대한 에러 처리를 할 수 있다.
```
if(class(err) == "try-error") {try 에러 발생 시 처리할 동작}
```

<br>

## 6.1.2 tryCatch() 함수의 사용

**`tryCatch()`** 함수
- `try()` 함수보다 복합한 처리를 할 수 있는 함수
```R
> args(tryCatch)
function (expr, ..., finally)
NULL
```
