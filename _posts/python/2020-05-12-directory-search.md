---
title: "디렉토리 탐색"
date: 2020-05-12
category:
  - python
tag :
  - directory search
sidebar:
  nav: sidebar-python
mathjax: "true"
author_profile: false
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
header:
  overlay_image: /assets/images/development.jpg
  overlay_filter: 0.5
comments: true  
---

> 파이썬을 활용한 디렉토리 탐색 방법 정리

<br>

# 1. 디렉토리 탐색

<br>

하위 디렉토리를 포함하고 있는 디렉토리에 들어 있는 파일명과 경로를 가져오는 방법에 대해 정리했다.

디렉토리 탐색 방법으로는 **재귀 함수를 이용하는 방법**과 **`os.walk()` 함수를 사용하는 방법** 2가지를 사용했다.

<br>

## 1.1 주요 함수

### 1.1.1 `os.listdir(경로)`

- 해당 `경로`에 있는 디렉토리 및 파일명을 리스트 형태로 반환한다.

<br>

```python
import os

ROOT_PATH = "..\\rawdata\\기업별 관련기사"

print(os.listdir(ROOT_PATH))
```

```
['IT', '_공통', '금융공기업', '금융그룹', '보험사', '은행', '증권사', '카드사', '핀테크']
```

<br>

### 1.1.2 `os.path.join(경로1, 경로2)`

- `경로1`과 `경로2`를 연결하여 전체 경로를 만들어 낸다.

```python
import os

ROOT_PATH = "..\\rawdata\\기업별 관련기사"

folder = os.listdir(ROOT_PATH)[0]
print(os.path.join(ROOT_PATH, folder))
```

```
..\rawdata\기업별 관련기사\IT
```

<br>

### 1.1.3 `str.endswith(끝문자열)`

- `str` 문자열 변수의 끝부분이 해당 `끝문자열`로 끝나는 지 확인한다.
- 파일명의 확장자를 체크할 때 활용할 수 있다.

```python
file_sample = "abcd.txt"

print(file_sample.endswith(".txt"))
print(file_sample.endswith(".md"))
```

```
True
False
```

<br>

### 1.1.4 `os.path.splitext(str)`

- `str` 문자열을 `파일명`과 `확장자`로 분리한다.
- 결과값을 `[-1]`을 통해 슬라이싱하면 확장자를 얻을 수 있다.

```python
import os

file_sample = "abcd.txt"
sample = "abcd"

print(os.path.splitext(file_sample))
print(os.path.splitext(file_sample)[-1])
print(os.path.splitext(sample))
```

```
('abcd', '.txt')
.txt
('abcd', '')
```

<br>

## 1.2 재귀 함수 이용 디렉토리 탐색


```python
import os

def search(dirname, saveList):
    filenames = os.listdir(dirname)
    for filename in filenames:
        full_filename = os.path.join(dirname, filename)
        if not full_filename.endswith(".md"):
            search(full_filename, saveList)
        else:
            if saveList is not None:
                saveList.append(full_filename)
```


```python
ROOT_PATH = "..\\rawdata\\기업별 관련기사"

md_file_list = []
search(ROOT_PATH, md_file_list)
#md_file_list
md_file_list[:10]
```


    ['..\\rawdata\\기업별 관련기사\\IT\\네이버\\20200416 네이버 먹거리, 우리가 키운다 vs 카카오 같이 키우실 분.md',
     '..\\rawdata\\기업별 관련기사\\IT\\우리에프아이에스\\20200421 창업부터 독립까지 밀어준다…사내벤처 3곳 키우는 우리금융.md',
     '..\\rawdata\\기업별 관련기사\\IT\\카카오\\20200416 네이버 먹거리, 우리가 키운다 vs 카카오 같이 키우실 분.md',
     "..\\rawdata\\기업별 관련기사\\_공통\\20200204 보험업계는 '제로성장'이라는데, 은행들은 왜 보험사를 사들일까.md",
     "..\\rawdata\\기업별 관련기사\\_공통\\20200206 '디지털' 속도 내는 보험업계…디지털보험사 줄잇는다.md",
     '..\\rawdata\\기업별 관련기사\\_공통\\20200206 ‘역대 호황’ 누린 은행들의 고민…“올해는 힘들다”.md',
     '..\\rawdata\\기업별 관련기사\\_공통\\20200206 “길 잃은 돈 잡아라”… 은행·핀테크 ‘소액 자산관리 전쟁’.md',
     '..\\rawdata\\기업별 관련기사\\_공통\\20200206 김정태의 승부수…금융지주 초대형IB경쟁 본격화.md',
     "..\\rawdata\\기업별 관련기사\\_공통\\20200219 '신탁상품' 못키운 한국…노인들 'DLF'로 몰았다.md",
     "..\\rawdata\\기업별 관련기사\\_공통\\20200219 '지수 ETF'로 피신하는 외국인·기관.md"]

<br>

## 1.3 `os.walk()` 이용 디렉토리 탐색


```python
import os

result = []

for (path, dir, files) in os.walk(ROOT_PATH):

    for filename in files:
        ext = os.path.splitext(filename)[-1] # os.path.splitext() : 파일명과 확장자 분리
        if ext == ".md":
            result.append(os.path.join(path, filename))

#result
result[:10]
```


    ['..\\rawdata\\기업별 관련기사\\IT\\네이버\\20200416 네이버 먹거리, 우리가 키운다 vs 카카오 같이 키우실 분.md',
     '..\\rawdata\\기업별 관련기사\\IT\\우리에프아이에스\\20200421 창업부터 독립까지 밀어준다…사내벤처 3곳 키우는 우리금융.md',
     '..\\rawdata\\기업별 관련기사\\IT\\카카오\\20200416 네이버 먹거리, 우리가 키운다 vs 카카오 같이 키우실 분.md',
     "..\\rawdata\\기업별 관련기사\\_공통\\20200204 보험업계는 '제로성장'이라는데, 은행들은 왜 보험사를 사들일까.md",
     "..\\rawdata\\기업별 관련기사\\_공통\\20200206 '디지털' 속도 내는 보험업계…디지털보험사 줄잇는다.md",
     '..\\rawdata\\기업별 관련기사\\_공통\\20200206 ‘역대 호황’ 누린 은행들의 고민…“올해는 힘들다”.md',
     '..\\rawdata\\기업별 관련기사\\_공통\\20200206 “길 잃은 돈 잡아라”… 은행·핀테크 ‘소액 자산관리 전쟁’.md',
     '..\\rawdata\\기업별 관련기사\\_공통\\20200206 김정태의 승부수…금융지주 초대형IB경쟁 본격화.md',
     "..\\rawdata\\기업별 관련기사\\_공통\\20200219 '신탁상품' 못키운 한국…노인들 'DLF'로 몰았다.md",
     "..\\rawdata\\기업별 관련기사\\_공통\\20200219 '지수 ETF'로 피신하는 외국인·기관.md"]

<br>

## 1.4 Github Cocde

- [https://github.com/sunghan-kim/Project-News-Article-Crawling/blob/master/skill/directory-search.ipynb](https://github.com/sunghan-kim/Project-News-Article-Crawling/blob/master/skill/directory-search.ipynb)

<br>

## 1.5 참고 링크

- [https://wikidocs.net/39](https://wikidocs.net/39)
- [https://itholic.github.io/python-listdir-glob/](https://itholic.github.io/python-listdir-glob/)
