---
title: "01장. Rstudio 설치 및 관리"
date: 2019-03-03
category:
  - R
tag :
  -
sidebar:
  nav: sidebar-R-part01
mathjax: "true"
author_profile: false
#toc: true
#toc_label: "Contents"
#toc_icon: "cog"
#toc_sticky: true
header:
  overlay_image: /assets/images/finance.jpg
  overlay_filter: 0.5
---
R, Rstudio, Rtools 설치와 Rstudio 구성, 스크립트 파일 관리, 프로젝트를 이용한 파일 관리, 패키지 설치 및 관리에 관한 내용을 정리한 글입니다.

<br>

# 1. R 언어 및 Rstudio 설치

## 1.1 다운로드 주소

- [R 다운로드](https://www.r-project.org/)
- [Rstudio 다운로드](https://www.rstudio.com)
- [Rtools 다운로드](https://cran.r-project.org/bin/windows/Rtools) (Windows 사용자만 설치 필요)

**주의 사항**

- 각각의 설치 파일이 위치한 경로에 한글이 포함되어 있으면 설치 과정에 문제가 발생할 수 있다.

<br><br>

# 2. Rstudio 구성 (Rstudio 사용법 익히기)

## 2.1 Rstudio 창 구성

### 2.1.1 Console

- R언어가 입력을 받고 출력을 주는 부분

### 2.1.2 Environment

- 데이터들의 정보를 저장하고 보여주는 곳
- 빠르게 정보 확인 가능

### 2.1.3 History

- Console창에서 실행했던 명령들이 기록되는 곳
- 빗자루 모양을 클릭하여 삭제 가능

### 2.1.4 Files

- 탐색기 역할

### 2.1.5 Plots

- 차트를 보여주는 창

### 2.1.6 Packages

- 패키지 검색
- 새로운 패키지 설치
- 설치된 패키지 업데이트 필요 여부 확인 및 업데이트 실시
- 패키지 삭제 또한 가능

### 2.1.7 Helps

- 함수의 설명서를 보여주는 곳
- Console 창에서 `?명령어` 를 입력하면 Helps 창에 해당 명령어의 설명서 내용이 나타난다.

### 2.1.8 Viewer

- Rmarkdown 이나 Shiny와 같이 결과물을 보여주는 곳

## 2.2 스크립트

- `Ctrl + Shift + n` 단축키를 사용하여 새로운 R 스크립트 생성
- 스크립트에서 명령어를 작성한 후 `Ctrl + Enter` 단축키를 실행하면 해당 스크립트에 작성된 명령이 Console 창에서 실행된다.

<br><br>

# 3. Rstudio의 유용한 설정

생략

<br><br>

# 4. 스크립트 파일 관리

## 4.1 `getwd()`

- 현재의 working directory 정보를 반환한다.

## 4.2 `source("스크립트파일명")`

- `source("")`만 입력하고 `Tab` 을 누르면 현재 위치에 있는 스크립트 파일을 선택할 수 있게끔 나타난다.
- 스크립트 파일을 선택하여 `source("스크립트파일명")` 명령을 실행하면 해당 스크립트파일 내에 있는 명령이 실행된다.

## 4.3 `Ctrl + Shift + s`

- 해당 스크립트내에 있는 모든 명령을 실행한다.

## 4.4 `Ctrl + Enter`

- 스크립트 내의 명령어를 한 줄씩 실행한다.
- 한 줄 실행 후 커서는 한 줄 아래로 이동하게 된다.

## 4.5 `setwd("경로")`

- 지정한 경로로 working directory 설정한다.

<br><br>

# 5. 프로젝트를 이용한 파일관리

- 폴더를 만들어서 스크립트파일과 데이터 파일을 관리

## Create Project

- New Directory 선택
- New Project 선택
- Directory Name 에 프로젝트명을 입력하고 Create Project 버튼을 클릭하면 Rstudio가 다시 실행된다.
- 우측 상단에 지정한 프로젝트명을 볼 수 있다.
- Files에 프로젝트명으로된 폴더가 생성된 것을 확인할 수 있다.
- 이렇게 하면 하나의 작업 단위를 한 폴더에서 작업할 수 있게 된다.
- .Rproj 파일을 클릭하면 해당 프로젝트가 실행된다.

<br><br>

# 6. 패키지 설치 및 관리

## 6.1 패키지 설치 방법

### 6.1.1 Rstudio 제공 기능 활용

- Packages 탭 사용
- 해당 탭에서 Install, Update 버튼 확인
- 아래 나타나는 목록은 현재 설치되어 있는 패키지 목록임

1) Install  

- Install 버튼 클릭
- Install from -> Repository (CRAN) : 인터넷이 연결된 환경에서 외부에서 설치
- Install from -> Package Archive File : 컴퓨터에 저장된 패키지 설치 파일(아카이브) 이용 설치
- Packages : 설치하려는 패키지명 입력 (ex. zoo)
- Install 버튼 클릭
- Packages 탭의 목록에서 설치한 패키지를 클릭하면 해당 패키지의 함수들에 대한 정보를 help 탭에서 확인할 수 있다.

2) update  

- CRAN에 패키지 버전과 로컬에 설치된 패키지의 버전을 비교하여 업데이트해준다.
- 패키지를 선택할 수도 있고, select all 버튼을 눌러 전체 패키지를 업데이트 할 수도 있다.
- 패키지의 버전을 항상 최신으로 유지하는 것을 권장한다.

3) delete  

- 패키지가 잘못 설치됐을 때 패키지 목록의 오른쪽에 x 버튼을 클릭한다.
- 패키지 삭제 후 `Session > Clear Workspace` 를 클릭한다. (Include hidden objects 체크)
- 그런 다음 `Session > Restart R` 을 클릭한다.
- 이렇게 하고 나서 다시 패키지를 설치하면 잘못 설치되어 에러가 발생한 것을 해결할 수 있다.

**주의사항**

- 패키지 라이브러리 경로에 한글이 포함되어 install이 안 될때가 있다.
- 그러면 `.libPaths("경로명")` 명령어를 실행한다.
- 경로명에는 한글이 포함되지 않은 경로명을 입력한다.
- 이렇게 하면 패키지 라이브러리 경로가 새로 지정되어 패키지를 설치할 수 있다.

### 6.1.2 코드 활용

1) `install.packages("패키지명")`  

- 패키지를 설치하는 명령어

2) `library("패키지명")`  

- 해당 패키지를 사용하겠다는 명령어

3) `remove.packages("패키지명")`  

- 해당 패키지 삭제
