---
title: "2.2 첫 번째 머신러닝 만들어 보기 - 붓꽃 품종 예측하기"
date: 2020-03-20
category:
  - ML
tag :
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

# v02. 첫 번째 머신러닝 만들어 보기 - 붓꽃 품종 예측하기

<br>

## 2.1 필요 라이브러리 임포트


```python
from sklearn.datasets import load_iris
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
import pandas as pd
```

<br>

## 2.2 데이터셋


```python
# 붓꽃 데이터 세트 로딩
iris = load_iris()

# iris.data는 Iris 데이터 세트에서 피처(feature)만으로 된 데이터를 numpy로 가지고 있음
iris_data = iris.data

# iris.target은 붓꽃 데이터 세트에서 레이블(결정 값) 데이터를 numpy로 가지고 있음
iris_label = iris.target
print('iris target값 : ', iris_label)
print('iris target명 : ', iris.target_names)
```

    iris target값 :  [0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
     0 0 0 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
     1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 2
     2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
     2 2]
    iris target명 :  ['setosa' 'versicolor' 'virginica']


<br>


```python
# 불꽃 데이터 세트를 자세히 보기 위해 DataFrame으로 변환
iris_df = pd.DataFrame(data=iris_data, columns=iris.feature_names)
iris_df['label'] = iris.target
iris_df.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
    .dataframe tbody tr th {
        vertical-align: top;
    }
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal length (cm)</th>
      <th>sepal width (cm)</th>
      <th>petal length (cm)</th>
      <th>petal width (cm)</th>
      <th>label</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



<br>

## 2.3 데이터셋 분리


```python
X_train, X_test, y_train, y_test = train_test_split(iris_data, iris_label,
                                                    test_size=0.2, random_state=11)
```

<br>

## 2.4 모델 객체 생성


```python
# DecisionTreeClassifier 객체 생성
dt_clf = DecisionTreeClassifier(random_state=11)
```

<br>

## 2.5 모델 학습


```python
# 학습 수행
dt_clf.fit(X_train, y_train)
```




    DecisionTreeClassifier(class_weight=None, criterion='gini', max_depth=None,
                max_features=None, max_leaf_nodes=None,
                min_impurity_decrease=0.0, min_impurity_split=None,
                min_samples_leaf=1, min_samples_split=2,
                min_weight_fraction_leaf=0.0, presort=False, random_state=11,
                splitter='best')



<br>

## 2.6 예측


```python
# 학습이 완료된 DecisionTreeClassifier 객체에서 테스트 데이터 세트로 예측 수행
pred = dt_clf.predict(X_test)
```

<br>

## 2.7 평가


```python
from sklearn.metrics import accuracy_score
print('예측 정확도 : {0:.4f}'.format(accuracy_score(y_test, pred)))
```

    예측 정확도 : 0.9333


<br>

## 2.8 붓꽃 데이터 세트로 분류를 예측한 프로세스 정리

### 2.8.1 데이터 세트 분리

- 데이터를 학습 데이터와 테스트 데이터로 분리

<br>

### 2.8.2 모델 학습

- 학습 데이터를 기반으로 ML 알고리즘을 적용해 모델을 학습

<br>

### 2.8.3 예측 수행

- 학습된 ML 모델을 이용해 테스트 데이터의 분류(즉, 붓꽃 종류)를 예측

<br>

### 2.8.4 평가

- 이렇게 예측된 결괏값과 테스트 데이터의 실제 결괏값을 비교해 ML 모델 성능을 평가
