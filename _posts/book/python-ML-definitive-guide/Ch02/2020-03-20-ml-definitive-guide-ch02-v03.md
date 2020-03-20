---
title: "2.3 사이킷런의 기반 프레임워크 익히기"
date: 2020-03-20
category:
  - scikit-learn
tag :
  - scikit-learn
sidebar:
  nav: sidebar-pythonMLDefinitiveGuide-ch02
mathjax: "true"
author_profile: false
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
header:
  overlay_image: /assets/images/dataScience.jpg
  overlay_filter: 0.5
comments: true  
---
 해당 포스트는 책 "파이썬 머신러닝 완벽 가이드"의 내용을 학습하여 정리한 글입니다.

<br><br>

# Ch02. 사이킷런으로 시작하는 머신러닝

<br>

# v03. 사이킷런의 기반 프레임워크 익히기

## 3.1 Estimator 이해 및 `fit()`, `predict()` 메서드

### 3.1.1 지도학습 프레임워크

#### 3.1.1.1 `Estimator`

- 지도학습의 모든 알고리즘을 구현한 클래스

<br>

#### 3.1.1.2 `~Classifier`

- 분류(Classification) 알고리즘이 구현된 클래스  

- `DecisionTreeClassifier`
- `RandomForestClassifier`
- `GradientBoostingClassifier`
- `GaussianNB`
- `SVC`

<br>

#### 3.1.1.3 `~Regressor`

- 회귀(Regression) 알고리즘이 구현된 클래스  

- `LinearRegression`
- `Ridge`
- `Lasso`
- `RandomForestRegressor`
- `GradientBoostingRegressor`

<br>

#### 3.1.1.4 `fit()`

- 지도학습 알고리즘을 학습시킬 때 사용되는 메서드

<br>

#### 3.1.1.5 `predict()`

- 지도학습 알고리즘을 이용하여 예측을 할 때 사용되는 메서드

<br>

### 3.1.2 비지도학습 프레임워크

#### 3.1.2.1 비지도학습

- 차원 축소
- 클러스터링
- 피처 추출(Feature Extraction)

<br>

#### 3.1.2.2 `fit()`

- 입력 데이터의 형태에 맞춰 데이터를 변환하기 위하나 사전 구조를 맞추는 작업

<br>

#### 3.1.2.3 `transform()`

- 입력 데이터의 차원 변환, 클러스터링, 피처 추출 등의 실제 작업을 수행

<br>

#### 3.1.2.4 `fit_transform()`

- `fit()`과 `transform()`을 하나로 결합한 메서드

<br>

## 3.2 사이킷런의 주요 모듈

### 3.2.1 예제 데이터

#### 3.2.1.1 `sklearn.datasets`

- 사이킷런에 내장되어 있는 예제로 제공하는 데이터 세트

<br>

### 3.2.2 피처 처리

#### 3.2.2.1 `sklearn.preprocessing`

- 데이터 전처리에 필요한 다양한 가공 기능 제공  
(문자열을 숫자형 코드 값으로 인코딩, 정규화, 스케일링 등)

<br>

#### 3.2.2.2 `sklearn.feature_selection`

- 알고리즘에 큰 영향을 미치는 피처를 우선순위대로 셀렉션 작업을 수행하는 다양한 기능 제공

<br>

#### 3.2.2.3 `sklearn.feature_extraction`

- 텍스트 데이터나 이미지 데이터의 벡터화된 피처를 추출하는 데 사용됨  
- ex) 텍스트 데이터에서 Count Vectorizer나 Tf-Idf Vectorizer 등을 새엉하는 기능 제공.  
  - `sklearn.feature_extraction.text` : 텍스트 데이터의 피처 추출 모듈  
  - `sklearn.feature_extraction.image` : 이미지 데이터의 피처 추출 모듈

<br>

### 3.2.3 피처 처리 & 차원축소

#### 3.2.3.1 `sklearn.decomposition`

- 차원 축소와 관련한 알고리즘을 지원하는 모듈.  
- PCA, NMF, Truncated SVD 등을 통해 차원 축소 기능을 수행할 수 있음

<br>

### 3.2.4 데이터 분리, 검증 & 파라미터 튜닝

#### 3.2.4.1 `sklearn.model_selection`

- 교차 검증을 위한 학습용/테스트용 분리, 그리드 서치(Grid Search)로 최적 파라미터 추출 등의 API 제공

<br>

### 3.2.5 평가

#### 3.2.5.1 `sklearn.metrics`

- 분류, 회귀, 클러스터링, 페어와이즈(Pairwise)에 대한 다양한 성능 측정 방법 제공.  
- Accuracy, Precision, Recall, ROC-AUC, RMSE 등 제공

<br>

### 3.2.6 ML 알고리즘

#### 3.2.6.1 `sklearn.ensemble`

- 앙상블 알고리즘 제공.  
- 랜덤 포레스트, 에이다 부스트, 그래디언트 부스팅 등을 제공

<br>

#### 3.2.6.2 `sklearn.linear_model`

- 선형 회귀, 릿지(Ridge), 라쏘(Lasso) 및 로지스틱 회귀 등 회귀 관련 알고리즘을 지원.  
- 또한 SGD(Stochastic Gradient Descent) 관련 알고리즘도 제공

<br>

#### 3.2.6.3 `sklearn.naive_bayes`

- 나이브 베이즈 알고리즘 제공.  
- 가우시안 NB, 다항 분포 NB 등.

<br>

#### 3.2.6.4 `sklearn.neighbors`

- 최근접 이웃 알고리즘 제공.  
- K-NN 등

<br>

#### 3.2.6.5 `sklearn.svm`

- 서포트 벡터 머신 알고리즘 제공

<br>

#### 3.2.6.6 `sklearn.tree`

- 의사 결정 트리 알고리즘 제공

<br>

#### 3.2.6.7 `sklearn.cluster`

- 비지도 클러스터링 알고리즘 제공.  
(K-평균, 계층형, DBSCAN 등)

<br>

### 3.2.7 유틸리티

#### 3.2.7.1 `sklearn.pipeline`

- 피처 처리 등의 변환과 ML 알고리즘 학습, 예측 등을 함께 묶어서 실행할 수 있는 유틸리티 제공

<br>

## 3.3 내장된 예제 데이터 세트

### 3.3.1 분류 or 회귀 연습용 예제 데이터

#### 3.3.1.1 `datasets.load_boston()`

- 회귀 용도  
- 미국 보스턴의 집 피처들과 가격에 대한 데이터 세트

<br>

#### 3.3.1.2 `datasets.load_breast_cancer()`

- 분류 용도  
- 위스콘신 유방암 피처들과 악성/은성 레이블 데이터 세트

<br>

#### 3.3.1.3 `datasets.load_diabetes()`

- 회귀 용도  
- 당뇨 데이터 세트

<br>

#### 3.3.1.4 `datasets.load_digits()`

- 분류 용도  
- 0에서 9까지 숫자의 이미지 픽셀 데이터 세트

<br>

#### 3.3.1.5 `datasets.load_iris()`

- 분류 용도  
- 붓꽃에 대한 피처를 가진 데이터 세트

<br>

### 3.3.2 fetch 계열의 명령

- 데이터의 크기가 커서 패키지에 처음부터 내장되어 있지 않고 인터넷에서 내려받아 홈 디렉토리 아래의 scikit_learn_data 라는 서브 디렉토리에 저장한 후 추후 불러들이는 데이터

<br>

#### 3.3.2.1 `fetch_covtype()`

- 회귀 분석용 토지 조사 자료

<br>

#### 3.3.2.2 `fetch_20newsgroup()`

- 뉴스 그룹 텍스트 자료

<br>

#### 3.3.2.3 `fetch_olivetti_faces()`

- 얼굴 이미지 자료

<br>

#### 3.3.2.4 `fetch_lfw_people()`

- 얼굴 이미지 자료

<br>

#### 3.3.2.5 `fetch_lfw_pairs()`

- 얼굴 이미지 자료

<br>

#### 3.3.2.6 `fetch_rcv1()`

- 로이터 뉴스 말뭉치

<br>

#### 3.3.2.7 `fetch_mldata()`

- ML 웹사이트에서 다운로드

<br>

### 3.3.3 분류와 클러스터링을 위한 표본 데이터 생성기

#### 3.3.3.1 `datasets.make_classifications()`

- 분류를 위한 데이터 세트를 만듬  
- 특히 높은 상관도, 불필요한 속성 등의 노이즈 효과를 위한 데이터를 무작위로 생성

<br>

#### 3.3.3.2 `datasets.make_blobs()`

- 클러스터링을 위한 데이터 세트를 무작위로 생성  
- 군집 지정 개수에 따라 여러 가지 클러스터링을 위한 데이터 세트를 쉽게 만들어 줌

<br>

### 3.3.4 연습용 예제 데이터의 구성

- 일반적으로 **딕셔너리 형태**로 되어 있음
- 키의 종류 :`data`, `target`, `target_name`, `feature_names`, `DESCR`

<br>

#### 3.3.4.1 `data`

- 피처의 데이터 세트를 가리킴  
- 넘파이 배열(ndarray) 타입

<br>

#### 3.3.4.2 `target`

- 분류 시 $$\rightarrow$$ 레이블 값 데이터 세트  
- 회귀 시 $$\rightarrow$$ 숫자 결괏값 데이터 세트  
- 넘파이 배열(ndarray) 타입

<br>

#### 3.3.4.3 `target_names`

- 개별 레이블의 이름을 나타냄  
- 넘파이 배열(ndarray) 또는 파이썬 리스트(list) 타입

<br>

#### 3.3.4.4 `feature_names`

- 피처의 이름들을 나타냄  
- 넘파이 배열(ndarray) 또는 파이썬 리스트(list) 타입

<br>

#### 3.3.4.5 `DESCR`

- 데이터 세트에 대한 설명과 각 피처의 설명을 나타냄  
- string 타입


```python
from sklearn.datasets import load_iris

iris_data = load_iris()
print(type(iris_data))
```

    <class 'sklearn.utils.Bunch'>


<br>


```python
keys = iris_data.keys()
print('붓꽃 데이터 세트의 키들 : ', keys)
```

    붓꽃 데이터 세트의 키들 :  dict_keys(['data', 'target', 'target_names', 'DESCR', 'feature_names'])


<br>


```python
print('\nfeature_names 의 type : ', type(iris_data.feature_names))
print('feature_names 의 shape : ', len(iris_data.feature_names))
print(iris_data.feature_names)

print('\ntarget_names 의 type : ', type(iris_data.target_names))
print('target_names 의 shape : ', len(iris_data.target_names))
print(iris_data.target_names)

print('\ndata 의 type : ', type(iris_data.data))
print('data 의 shape : ', len(iris_data.data))
print(iris_data.data)

print('\ntarget 의 type : ', type(iris_data.target))
print('target 의 shape : ', len(iris_data.target))
print(iris_data.target)
```


    feature_names 의 type :  <class 'list'>
    feature_names 의 shape :  4
    ['sepal length (cm)', 'sepal width (cm)', 'petal length (cm)', 'petal width (cm)']

    target_names 의 type :  <class 'numpy.ndarray'>
    target_names 의 shape :  3
    ['setosa' 'versicolor' 'virginica']

    data 의 type :  <class 'numpy.ndarray'>
    data 의 shape :  150
    [[5.1 3.5 1.4 0.2]
     [4.9 3.  1.4 0.2]
     [4.7 3.2 1.3 0.2]
    	...
     [6.5 3.  5.2 2. ]
     [6.2 3.4 5.4 2.3]
     [5.9 3.  5.1 1.8]]

    target 의 type :  <class 'numpy.ndarray'>
    target 의 shape :  150
    [0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
     0 0 0 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
     1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 2
     2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
     2 2]
