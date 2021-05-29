---
title: "패키지 설치 및 관리"
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

# 5. 패키지 설치 및 관리

## 5.1 패키지 설치 방법

### 5.1.1 Rstudio 제공 기능 활용

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

### 5.1.2 코드 활용

1) `install.packages("패키지명")`  

- 패키지를 설치하는 명령어

2) `library("패키지명")`  

- 해당 패키지를 사용하겠다는 명령어

3) `remove.packages("패키지명")`  

- 해당 패키지 삭제
