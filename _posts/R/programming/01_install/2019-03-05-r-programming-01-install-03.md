---
title: "스크립트 파일 관리"
date: 2019-03-05
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
> R > Programming > Install

# 3. 스크립트 파일 관리

## 3.1 `getwd()`

- 현재의 working directory 정보를 반환한다.

## 3.2 `source("스크립트파일명")`

- `source("")`만 입력하고 `Tab` 을 누르면 현재 위치에 있는 스크립트 파일을 선택할 수 있게끔 나타난다.
- 스크립트 파일을 선택하여 `source("스크립트파일명")` 명령을 실행하면 해당 스크립트파일 내에 있는 명령이 실행된다.

## 3.3 `Ctrl + Shift + s`

- 해당 스크립트내에 있는 모든 명령을 실행한다.

## 3.4 `Ctrl + Enter`

- 스크립트 내의 명령어를 한 줄씩 실행한다.
- 한 줄 실행 후 커서는 한 줄 아래로 이동하게 된다.

## 3.5 `setwd("경로")`

- 지정한 경로로 working directory 설정한다.
