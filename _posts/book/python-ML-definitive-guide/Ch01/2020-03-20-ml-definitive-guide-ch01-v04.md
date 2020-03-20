---
title: "1.4 데이터 핸들링 - 판다스"
date: 2020-03-20
category:
  - Python
tag :
  - Pandas
  - Series
  - DataFrame
  - DataFrame.sort_values
  - DataFrame.groupby
  - Null Data Handling
sidebar:
  nav: sidebar-pythonMLDefinitiveGuide-ch01
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

# Ch01. 파이썬 기반의 머신러닝과 생태계 이해

<br>

# v04. 데이터 핸들링 - 판다스

<br>

## 4.1 판다스 시작 - 파일을 DataFrame으로 로딩, 기본 API


```python
import pandas as pd
import warnings
warnings.filterwarnings('ignore')
```


```python
titanic_df = pd.read_csv('./data/titanic_train.csv')
titanic_df.head(3)
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>



<br>

### 4.1.1 `DataFrame.shape`

- DataFrame의 행과 열의 크기 확인


```python
print('DataFrame 크기 : ', titanic_df.shape)
```

    DataFrame 크기 :  (891, 12)


<br>

### 4.1.2 `DataFrame.info()`

- 총 데이터 건수, 데이터 타입, Null 건수 확인


```python
titanic_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 12 columns):
    PassengerId    891 non-null int64
    Survived       891 non-null int64
    Pclass         891 non-null int64
    Name           891 non-null object
    Sex            891 non-null object
    Age            714 non-null float64
    SibSp          891 non-null int64
    Parch          891 non-null int64
    Ticket         891 non-null object
    Fare           891 non-null float64
    Cabin          204 non-null object
    Embarked       889 non-null object
    dtypes: float64(2), int64(5), object(5)
    memory usage: 83.7+ KB


<br>

### 4.1.3 `DataFrame.describe()`

- 숫자형(int, float 등) 컬럼의 부포도 조사 (자동으로 object 타입의 컬럼은 출력에서 제외)


```python
titanic_df.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Fare</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>714.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>446.000000</td>
      <td>0.383838</td>
      <td>2.308642</td>
      <td>29.699118</td>
      <td>0.523008</td>
      <td>0.381594</td>
      <td>32.204208</td>
    </tr>
    <tr>
      <th>std</th>
      <td>257.353842</td>
      <td>0.486592</td>
      <td>0.836071</td>
      <td>14.526497</td>
      <td>1.102743</td>
      <td>0.806057</td>
      <td>49.693429</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.420000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>223.500000</td>
      <td>0.000000</td>
      <td>2.000000</td>
      <td>20.125000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>7.910400</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>446.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>28.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>14.454200</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>668.500000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>38.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>31.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>891.000000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>80.000000</td>
      <td>8.000000</td>
      <td>6.000000</td>
      <td>512.329200</td>
    </tr>
  </tbody>
</table>
</div>



- count : Not Null인 데이터 건수

<br>

해당 숫자 컬럼이 숫자형 카테고리 컬럼인 지를 판단할 수 있다.

- Survived 컬럼
  - min = 25% = 50% = 75% = 0
  - max = 1
  - 0과 1로 이루어진 숫자형 카테고리 컬럼  

- Pclass 컬럼
  - min = 1
  - 25% = 2
  - 50% = 75% = max = 3
  - 1, 2, 3으로 이뤄진 숫자형 카테고리 컬럼

<br>

<br>

### 4.1.4 `Series.value_counts()`

- 해당 컬럼값의 유형과 건수 확인
- 지정된 컬럼의 데이터값 건수를 반환
- 데이터의 분포도를 확인하는 데 매우 유용한 함수


```python
value_counts = titanic_df['Pclass'].value_counts()
print(value_counts)
```

    3    491
    1    216
    2    184
    Name: Pclass, dtype: int64


- 많은 건수 순서로 정렬되어 값을 반환

<br>

### 4.1.5 `[]` 연산자

- DataFrame의 `[]` 연산자 내부에 컬럼명을 입력하면 해당 컬럼에 해당하는 Series 객체를 반환


```python
titanic_pclass = titanic_df['Pclass']
print(type(titanic_pclass))
```

    <class 'pandas.core.series.Series'>


<br>

### 4.1.6 `Series`

- Index와 단 하나의 컬럼으로 구성된 데이터 세트


```python
titanic_pclass.head()
```




    0    3
    1    1
    2    3
    3    1
    4    3
    Name: Pclass, dtype: int64



<br>

`value_counts()` 메서드는 Series 객체에서만 정의되어 있다.  
DataFrame은 `value_counts()` 메서드를 가지고 있지 않음


```python
value_counts = titanic_df['Pclass'].value_counts()
print(type(value_counts))
print(value_counts)
```

    <class 'pandas.core.series.Series'>
    3    491
    1    216
    2    184
    Name: Pclass, dtype: int64


`value_counts()`가 반환하는 데이터 타입 역시 Series 객체이다.

<br>

## 4.2 DataFrame과 리스트, 딕셔너리, 넘파이 ndarray 상호 변환

### 4.2.1 넘파이 ndarray, 리스트, 딕셔러니를 DataFrame으로 변환하기


```python
import numpy as np

# 1차원 형태의 리스트와 넘파이 ndarray -> DataFrame
col_name1 = ['col1']
list1 = [1, 2, 3]
array1 = np.array(list1)
print('array1 shape : ', array1.shape)
```

    array1 shape :  (3,)


<br>


```python
# 1차원 리스트 -> DataFrame
df_list1 = pd.DataFrame(list1, columns=col_name1)
print('1차원 리스트로 만든 DataFrame : \n', df_list1)
```

    1차원 리스트로 만든 DataFrame :
        col1
    0     1
    1     2
    2     3


<br>


```python
# 1차원 넘파이 ndarray -> DataFrame
df_array1 = pd.DataFrame(array1, columns=col_name1)
print('1차원 ndarray로 만든 DataFrame : \n', df_array1)
```

    1차원 ndarray로 만든 DataFrame :
        col1
    0     1
    1     2
    2     3


<br>


```python
# 2행 3열 형태의 리스트와 넘파이 ndarray -> DataFrame

# 3개의 컬럼명이 필요함
col_name2 = ['col1', 'col2', 'col3']

# 2행x3열 형태의 리스트와 ndarray 생성
list2 = [[1, 2, 3],
         [11, 12, 13]]
array2 = np.array(list2)
print('array2 shape : ', array2.shape)
```

    array2 shape :  (2, 3)


<br>


```python
# 2차원 리스트 -> DataFrame
df_list2 = pd.DataFrame(list2, columns=col_name2)
print('2차원 리스트로 만든 DataFrame : \n', df_list2)
```

    2차원 리스트로 만든 DataFrame :
        col1  col2  col3
    0     1     2     3
    1    11    12    13


<br>


```python
# 2차원 넘파이 ndarray -> DataFrame
df_array2 = pd.DataFrame(array2, columns=col_name2)
print('2차원 ndarray로 만든 DataFrame : \n', df_array2)
```

    2차원 ndarray로 만든 DataFrame :
        col1  col2  col3
    0     1     2     3
    1    11    12    13


<br>


```python
# 딕셔너리 -> DataFrame
# Key는 문자열 컬럼명으로 매핑, Value는 리스트 형(또는 ndarray) 컬럼 데이터로 매핑
dict = {'col1': [1, 11], 'col2': [2, 22], 'col3': [3, 33]}
df_dict = pd.DataFrame(dict)
print('딕셔너리로 만든 DataFrame : \n', df_dict)
```

    딕셔너리로 만든 DataFrame :
        col1  col2  col3
    0     1     2     3
    1    11    22    33


<br>

### 4.2.2 DataFrame을 넘파이 ndarray, 리스트, 디셔너리로 변환하기

#### 4.2.2.1 DataFrame $$\rightarrow$$ ndarray

`DataFrame.values`

- DataFrame 객체를 ndarray 객체로 변환


```python
# DataFrame을 ndarray로 변환
array3 = df_dict.values
print('df_dict.values 타입 : ', type(array3))
print('df_dict.values shapes : ', array3.shape)
print(array3)
```

    df_dict.values 타입 :  <class 'numpy.ndarray'>
    df_dict.values shapes :  (2, 3)
    [[ 1  2  3]
     [11 22 33]]


<br>

#### 4.2.2.2 DataFrame $$\rightarrow$$ List

`DataFrame.values.tolist()`


```python
# DataFrame을 리스트로 변환
list3 = df_dict.values.tolist()
print('df_dict.values.tolist() 타입 : ', type(list3))
print(list3)
```

    df_dict.values.tolist() 타입 :  <class 'list'>
    [[1, 2, 3], [11, 22, 33]]


<br>

#### 4.2.2.3 DataFrame $$\rightarrow$$ Dictionary

`DataFrame.to_dict('list')`


```python
# DataFrame을 딕셔너리로 변환
dict3 = df_dict.to_dict('list')
print('df_dict.values.to_dict() 타입 : ', type(dict3))
print(dict3)
```

    df_dict.values.to_dict() 타입 :  <class 'dict'>
    {'col1': [1, 11], 'col2': [2, 22], 'col3': [3, 33]}


<br>

## 4.3 DataFrame의 컬럼 데이터 세트 생성과 수정

### 4.3.1 새로운 컬럼 추가


```python
titanic_df['Age_0'] = 0
titanic_df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>Age_0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
titanic_df['Age_by_10'] = titanic_df['Age'] * 10
titanic_df['Family_No'] = titanic_df['SibSp'] + titanic_df['Parch'] + 1
titanic_df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>Age_0</th>
      <th>Age_by_10</th>
      <th>Family_No</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>0</td>
      <td>220.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>0</td>
      <td>380.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>0</td>
      <td>260.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



<br>

### 4.3.1 기존 컬럼 수정


```python
titanic_df['Age_by_10'] = titanic_df['Age_by_10'] + 100
titanic_df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>Age_0</th>
      <th>Age_by_10</th>
      <th>Family_No</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>0</td>
      <td>320.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>0</td>
      <td>480.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>0</td>
      <td>360.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



<br>

## 4.4 DataFrame 데이터 삭제

### 4.4.1 `DataFrame.drop()`

```
DataFrame(labels=None, axis=0, ..., inplace=False, ...)
```

<br>

#### 4.4.1.1 `axis`

- `axis=0`
  - 로우 방향 축
  - 특정 로우를 드롭하겠다.
  - 이상치 데이터를 삭제하는 경우 주로 사용  

- `axis=1` : 컬럼 방향 축
  - 컬럼을 드롭하겠다.
  - 기존 컬럼 값을 가공해 새로운 컬럼을 만들고 삭제하는 경우가 많음


```python
# Age_0 컬럼 삭제
titanic_drop_df = titanic_df.drop('Age_0', axis=1)
titanic_drop_df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>Age_by_10</th>
      <th>Family_No</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>320.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>480.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>360.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.4.1.2 `inplace`

- `inplace=False`
  - `drop()` 함수의 `inplace` 인자의 디폴트 값
  - 자기 자신의 DataFrame의 데이터는 삭제하지 않고, 삭제된 결과 DataFrame을 반환  

- `inplace=True`
  - 자신의 DataFrame의 데이터를 삭제

<br>

#### 4.4.1.3 `labels`

- 컬럼명을 입력받는 인자
- 여러 개의 컬럼을 삭제하고 싶으면 **리스트 형태**로 삭제하고자 하는 컬럼명을 입력


```python
titanic_df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>Age_0</th>
      <th>Age_by_10</th>
      <th>Family_No</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>0</td>
      <td>320.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>0</td>
      <td>480.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>0</td>
      <td>360.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
# Age_0, Age_by_10, Family_No 컬럼 삭제
drop_result = titanic_df.drop(['Age_0', 'Age_by_10', 'Family_No'], axis=1, inplace=True)
print('inplace=True 로 drop 후 반환된 값 : ', drop_result)
titanic_df.head(3)
```

    inplace=True 로 drop 후 반환된 값 :  None





<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>



<br>

`drop()` 시 `inplace=True`로 설정하면 반환값이 `None`(아무 값도 아님)이 된다.  
`inplace=True`로 설정한 채로 반환 값을 다시 자신의 DataFrame 객체로 할당하면 안된다.  


```python
# 맨 앞 3개 데이터 삭제
pd.set_option('display.width', 1000)
pd.set_option('display.max_colwidth', 15)

print('### before axis 0 drop ###')
print(titanic_df.head(3))

titanic_df.drop([0, 1, 2], axis=0, inplace=True)

print('### after axis 0 drop ###')
print(titanic_df.head(3))
```

    ### before axis 0 drop ###
       PassengerId  Survived  Pclass            Name     Sex   Age  SibSp  Parch          Ticket     Fare Cabin Embarked
    0            1         0       3  Braund, Mr....    male  22.0      1      0       A/5 21171   7.2500   NaN        S
    1            2         1       1  Cumings, Mr...  female  38.0      1      0        PC 17599  71.2833   C85        C
    2            3         1       3  Heikkinen, ...  female  26.0      0      0  STON/O2. 31...   7.9250   NaN        S
    ### after axis 0 drop ###
       PassengerId  Survived  Pclass            Name     Sex   Age  SibSp  Parch  Ticket     Fare Cabin Embarked
    3            4         1       1  Futrelle, M...  female  35.0      1      0  113803  53.1000  C123        S
    4            5         0       3  Allen, Mr. ...    male  35.0      0      0  373450   8.0500   NaN        S
    5            6         0       3  Moran, Mr. ...    male   NaN      0      0  330877   8.4583   NaN        Q


<br>

## 4.5 Index 객체

### 4.5.1 `DataFrame.index`, `Series.index`

- `DataFrame.index` 또는 `Series.index`로 Index 객체 추출.  


```python
# 원본 파일 다시 로딩
titanic_df = pd.read_csv('./data/titanic_train.csv')

# Index 객체 추출
indexes = titanic_df.index
print(indexes)
print('DataFrame.index의 타입 : ', type(titanic_df.index))
```

    RangeIndex(start=0, stop=891, step=1)
    DataFrame.index의 타입 :  <class 'pandas.core.indexes.range.RangeIndex'>


<br>

### 4.5.2 `DataFrame.index.values`

- `DataFrame.index.values` 로 Index 객체의 값 확인


```python
# Index 객체를 실제 값 array로 변환
print('indexes.values의 타입 : ', type(indexes.values))
print('\nIndex 객체 array값:\n', indexes.values)
```

    indexes.values의 타입 :  <class 'numpy.ndarray'>

    Index 객체 array값:
     [  0   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17
      18  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35
      ...
     846 847 848 849 850 851 852 853 854 855 856 857 858 859 860 861 862 863
     864 865 866 867 868 869 870 871 872 873 874 875 876 877 878 879 880 881
     882 883 884 885 886 887 888 889 890]


<br>

### 4.5.3 Index 객체의 식별성 데이터

- Index 객체는 식별성 데이터를 1차원 array로 가지고 있다.  
- ndarray와 유사하게 단일 값 반환 및 슬라이싱 가능


```python
print(type(indexes.values))
print(indexes.values.shape)
print(indexes[:5].values)
print(indexes.values[:5])
print(indexes[6])
```

    <class 'numpy.ndarray'>
    (891,)
    [0 1 2 3 4]
    [0 1 2 3 4]
    6


<br>

### 4.5.4 Index 객체의 수정

- 한 번 만들어진 Index 객체는 함부로 변경할 수 없다.


```python
# indexes[0] = 5
```

<br>

### 4.5.5 Index 객체의 연산 제외

- Series 객체에 연산 함수를 적용할 때 Index는 연산에서 제외됨(오직 식별용으로만 사용)


```python
series_fair = titanic_df['Fare']
print('Fair Series max 값 : ', series_fair.max())
print('Fair Series sum 값 : ', series_fair.sum())
print('sum() Fair Series : ', sum(series_fair))
print('Fair Series + 3 : \n', (series_fair + 3).head(3))
```

    Fair Series max 값 :  512.3292
    Fair Series sum 값 :  28693.9493
    sum() Fair Series :  28693.949299999967
    Fair Series + 3 :
     0    10.2500
    1    74.2833
    2    10.9250
    Name: Fare, dtype: float64


<br>

### 4.5.6 `DataFrame.reset_index()` 또는 `Series.reset_index()`

- 새롭게 인덱스를 연속 숫자형으로 할당
- 기존 인덱스는 'index'라는 새로운 컬럼명으로 추가됨


```python
titanic_reset_df = titanic_df.reset_index(inplace=False)
titanic_reset_df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr....</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mr...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, ...</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 31...</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>



<br>

- Series 객체에 `reset_index()` 함수를 적용하면 DataFrame 객체로 변함


```python
print('### before reset_index ###')
value_counts = titanic_df['Pclass'].value_counts()
print(value_counts)
print('value_counts 객체 변수 타입 : ', type(value_counts))

new_value_counts = value_counts.reset_index(inplace=False)

print('### After reset_index ###')
print(new_value_counts)
print('new_value_counts 객체 변수 타입 : ', type(new_value_counts))
```

    ### before reset_index ###
    3    491
    1    216
    2    184
    Name: Pclass, dtype: int64
    value_counts 객체 변수 타입 :  <class 'pandas.core.series.Series'>
    ### After reset_index ###
       index  Pclass
    0      3     491
    1      1     216
    2      2     184
    new_value_counts 객체 변수 타입 :  <class 'pandas.core.frame.DataFrame'>


<br>

- `reset_index()` 의 parameter 중 `drop=True`로 설정하면 기존 인덱스는 새로운 컬럼으로 추가되지 않고 삭제(drop)됨
- Series 객체는 그대로 유지


```python
print('### before reset_index(drop=True) ###')
value_counts1 = titanic_df['Pclass'].value_counts()
print(value_counts1)
print('value_counts 객체 변수 타입 : ', type(value_counts1))

new_value_counts1 = value_counts.reset_index(inplace=False, drop=True)

print('### After reset_index ###')
print(new_value_counts1)
print('new_value_counts 객체 변수 타입 : ', type(new_value_counts1))
```

    ### before reset_index(drop=True) ###
    3    491
    1    216
    2    184
    Name: Pclass, dtype: int64
    value_counts 객체 변수 타입 :  <class 'pandas.core.series.Series'>
    ### After reset_index ###
    0    491
    1    216
    2    184
    Name: Pclass, dtype: int64
    new_value_counts 객체 변수 타입 :  <class 'pandas.core.series.Series'>


<br>

# 4.6 데이터 셀렉션 및 필터링

- 넘파이의 인덱싱
  - `[]` 연산자 내 단일 값 추출, 슬라이싱, 팬시 인덱싱, 불린 인덱싱  

- 판다스 인덱싱  
  - `ix[]`, `iloc[]`, `loc[]` 연산자 이용

<br>

### 4.6.1 DataFrame의 `[]` 연산자

- 넘파이의 `[]` 연산자와 비교.  
- **DataFrame 뒤에 있는 `[]`는 컬럼만 지정할 수 있는 '컬럼 지정 연산자'로 이해**


```python
print('단일 컬럼 데이터 추출 : \n', titanic_df['Pclass'].head(3))
print('\n여러 컬럼의 데이터 추출 : \n', titanic_df[['Survived', 'Pclass']].head(3))
#print('[] 안에 숫자 index는 KeyError 오류 발생 : \n', titanic_df[0])
```

    단일 컬럼 데이터 추출 :
     0    3
    1    1
    2    3
    Name: Pclass, dtype: int64

    여러 컬럼의 데이터 추출 :
        Survived  Pclass
    0         0       3
    1         1       1
    2         1       3


<br>

#### 4.6.1.1 `[]`연산자 슬라이싱

- DataFrame의 `[]` 연산자 안에 슬라이싱 이용 가능 (권장하지 않는 방법)


```python
titanic_df[0:2]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr....</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mr...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.6.1.2 `[]` 연산자 불린 인덱싱

- DataFrame 객체의 `[]` 연산자 내의 불린 인덱싱 사용 가능 (자주 사용하는 방법)


```python
titanic_df[titanic_df['Pclass'] == 3].head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr....</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, ...</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 31...</td>
      <td>7.925</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. ...</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.050</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>



<br>

### 4.6.2 DataFrame `ix[]` 연산자

- `DataFrame.ix[행 인덱스, 열 인덱스]`
  - 컬럼 위치(position) 기반 인덱싱  
  - 컬럼 위치 기반 인덱싱 연산자인 `iloc[]`로 대체됨  

- `DataFrame.ix[행 인덱스, 열 이름]`
  - 컬럼 명칭(label) 기반 인덱싱  
  - 컬럼 명칭 기반 인덱싱 연산자인 `loc[]`로 대체됨


```python
print('컬럼 위치 기반 인덱싱 데이터 추출 : ', titanic_df.ix[0, 2])
print('컬럼 이름 기반 인덱싱 데이터 추출 : ', titanic_df.ix[0, 'Pclass'])
```

    컬럼 위치 기반 인덱싱 데이터 추출 :  3
    컬럼 이름 기반 인덱싱 데이터 추출 :  3


<br>

DataFrame의 `ix[]` 연산자는 넘파이 ndarray의 `[]` 연산자와 동일하게 아래와 같은 기능 사용 가능

- 단일 지정 인덱싱
- 슬라이싱
- 불린 인덱싱
- 팬시 인덱싱


```python
# 예제 데이터
data = {'Name': ['Chulmin', 'Eunkyung', 'Jinwoong', 'Soobeom'],
        'Year': [2011, 2016, 2015, 2015],
        'Gender': ['Male', 'Female', 'Male', 'Male']
       }

data_df = pd.DataFrame(data, index=['one', 'two', 'three', 'four'])
data_df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Year</th>
      <th>Gender</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>Chulmin</td>
      <td>2011</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>two</th>
      <td>Eunkyung</td>
      <td>2016</td>
      <td>Female</td>
    </tr>
    <tr>
      <th>three</th>
      <td>Jinwoong</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>four</th>
      <td>Soobeom</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
data_df.ix[0,0]
```




    'Chulmin'



<br>


```python
data_df.ix['one', 0]
```




    'Chulmin'



<br>


```python
data_df.ix[3, 'Name']
```




    'Soobeom'



<br>


```python
data_df.ix[0:2, [0,1]]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>Chulmin</td>
      <td>2011</td>
    </tr>
    <tr>
      <th>two</th>
      <td>Eunkyung</td>
      <td>2016</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
try:
    data_df.ix[0:2, [0,3]]
except:
    print('error')
```

    error


<br>


```python
data_df.ix[0:3, ['Name', 'Year']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>Chulmin</td>
      <td>2011</td>
    </tr>
    <tr>
      <th>two</th>
      <td>Eunkyung</td>
      <td>2016</td>
    </tr>
    <tr>
      <th>three</th>
      <td>Jinwoong</td>
      <td>2015</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
data_df.ix[:]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Year</th>
      <th>Gender</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>Chulmin</td>
      <td>2011</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>two</th>
      <td>Eunkyung</td>
      <td>2016</td>
      <td>Female</td>
    </tr>
    <tr>
      <th>three</th>
      <td>Jinwoong</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>four</th>
      <td>Soobeom</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
data_df.ix[:, :]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Year</th>
      <th>Gender</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>Chulmin</td>
      <td>2011</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>two</th>
      <td>Eunkyung</td>
      <td>2016</td>
      <td>Female</td>
    </tr>
    <tr>
      <th>three</th>
      <td>Jinwoong</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>four</th>
      <td>Soobeom</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
data_df.ix[data_df.Year >= 2014]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Year</th>
      <th>Gender</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>two</th>
      <td>Eunkyung</td>
      <td>2016</td>
      <td>Female</td>
    </tr>
    <tr>
      <th>three</th>
      <td>Jinwoong</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>four</th>
      <td>Soobeom</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
  </tbody>
</table>
</div>



<br>

### 4.6.3 명칭 기반 인덱싱과 위치 기반 인덱싱의 구분


```python
# data_df를 reset_index()로 새로운 숫자형 인덱스를 생성
data_df_reset = data_df.reset_index()
data_df_reset = data_df_reset.rename(columns={'index': 'old_index'})

# 인덱스값에 1을 더해서 1부터 시작하는 새로운 인덱스값 생성
data_df_reset.index = data_df_reset.index+1
data_df_reset
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>old_index</th>
      <th>Name</th>
      <th>Year</th>
      <th>Gender</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>one</td>
      <td>Chulmin</td>
      <td>2011</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>2</th>
      <td>two</td>
      <td>Eunkyung</td>
      <td>2016</td>
      <td>Female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>three</td>
      <td>Jinwoong</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>4</th>
      <td>four</td>
      <td>Soobeom</td>
      <td>2015</td>
      <td>Male</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
#data_df_reset.ix[0, 1]
```

<br>

인덱스가 integer형인 경우 `ix[0,1]`은 행 위치 값으로 위치 기반 인덱스값을 사용하는 것이 아니라 DataFrame의 인덱스값을 사용.  
인덱스값이 0인 key는 찾을 수 없기 때문에 에러 발생.  
따라서 `ix[1,1]`을 적용해야 첫 번째 행(인덱스값 1)의 2번째 열 위치에 있는 데이터값을 반환


```python
data_df_reset.ix[1,1]
```




    'Chulmin'



<br>

**명칭 기반과 위치 기반의 데이터 형이 서로 같을 경우 명칭 기반이 우선한다.**

`ix[]`의 경우 행과 열 위치에 명칭과 위치 기반 인덱싱 모두를 허용한다.  
이 때문에 혼선이 생길 수 있기 때문에 새롭게 명칭 기반 인덱싱 연산자인 `loc[]`와 위치 기반 인덱싱인 `iloc[]` 연산자를 도입해 이들의 구분을 명확히 하게 됨

<br>

### 4.6.4 DataFrame `iloc[]` 연산자

`iloc[]`

- 위치 기반 인덱싱만 허용
- 행과 열 값으로 integer 또는 integer형의 슬라이싱, 팬시 리스트 값을 입력
- 불린 인덱싱은 조건을 기술하므로 이에 제약받지 않음 (불린 인덱싱 사용 가능)


```python
data_df.iloc[0,0]
```




    'Chulmin'



<br>


```python
# 위치 인덱싱이 아닌 명칭 입력 시 오류 발생
try:
    data_df.iloc[0, 'Name']
except:
    print("error")
```

    error


<br>


```python
# 문자열 인덱스를 행 위치에 입력해도 오류 발생
try:
    data_df.iloc['one', 0]
except:
    print("error")
```

    error


<br>


```python
data_df_reset.iloc[0, 1]
```




    'Chulmin'



<br>

### 4.6.5 DataFrame `loc[]` 연산자

`loc[]`

- 명칭 기반 데이터 추출
- 행 위치 : DataFrame index 값
- 열 위치 : 컬럼명


```python
data_df.loc['one', 'Name']
```




    'Chulmin'



<br>


```python
data_df_reset.loc[1, 'Name']
```




    'Chulmin'



<br>


```python
# data_df_reset에는 인덱스값이 0인 행이 없으므로 오류 반환
try:
    data_df_reset.loc[0, 'Name']
except:
    print("error")
```

    error


<br>

`loc[]`에 슬라이싱 기호 '`:`' 적용 시 주의 사항

- `loc[]`에 슬라이싱 기호를 적용하면 종료값-1이 아니라 종료값까지 포함하는 것을 의미


```python
print('명칭 기반 ix slicing\n', data_df.ix['one':'two', 'Name'], '\n')
print('위치 기반 iloc slicing\n', data_df.iloc[0:1, 0], '\n')
print('명칭 기반 loc slicing\n', data_df.loc['one':'two', 'Name'])
```

    명칭 기반 ix slicing
     one     Chulmin
    two    Eunkyung
    Name: Name, dtype: object

    위치 기반 iloc slicing
     one    Chulmin
    Name: Name, dtype: object

    명칭 기반 loc slicing
     one     Chulmin
    two    Eunkyung
    Name: Name, dtype: object


<br>


```python
print(data_df_reset.loc[1:2, 'Name'])
```

    1     Chulmin
    2    Eunkyung
    Name: Name, dtype: object


<br>


```python
print(data_df.ix[1:2, 'Name'])
```

    two    Eunkyung
    Name: Name, dtype: object


<br>

### 4.6.6 불린 인덱싱

- `[]`, `ix[]`, `loc[]` 공통 지원.  
- `iloc[]`의 경우 정수형 값이 아닌 불린 값에 대해서는 지원하지 않음 (불린 인덱싱이 지원되지 않는다.)


```python
titanic_df = pd.read_csv('./data/titanic_train.csv')
titanic_boolean = titanic_df[titanic_df['Age'] > 60]
print(type(titanic_boolean))
titanic_boolean
```

    <class 'pandas.core.frame.DataFrame'>





<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>33</th>
      <td>34</td>
      <td>0</td>
      <td>2</td>
      <td>Wheadon, Mr...</td>
      <td>male</td>
      <td>66.0</td>
      <td>0</td>
      <td>0</td>
      <td>C.A. 24579</td>
      <td>10.5000</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>54</th>
      <td>55</td>
      <td>0</td>
      <td>1</td>
      <td>Ostby, Mr. ...</td>
      <td>male</td>
      <td>65.0</td>
      <td>0</td>
      <td>1</td>
      <td>113509</td>
      <td>61.9792</td>
      <td>B30</td>
      <td>C</td>
    </tr>
    <tr>
      <th>96</th>
      <td>97</td>
      <td>0</td>
      <td>1</td>
      <td>Goldschmidt...</td>
      <td>male</td>
      <td>71.0</td>
      <td>0</td>
      <td>0</td>
      <td>PC 17754</td>
      <td>34.6542</td>
      <td>A5</td>
      <td>C</td>
    </tr>
    <tr>
      <th>116</th>
      <td>117</td>
      <td>0</td>
      <td>3</td>
      <td>Connors, Mr...</td>
      <td>male</td>
      <td>70.5</td>
      <td>0</td>
      <td>0</td>
      <td>370369</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
    </tr>
    <tr>
      <th>170</th>
      <td>171</td>
      <td>0</td>
      <td>1</td>
      <td>Van der hoe...</td>
      <td>male</td>
      <td>61.0</td>
      <td>0</td>
      <td>0</td>
      <td>111240</td>
      <td>33.5000</td>
      <td>B19</td>
      <td>S</td>
    </tr>
    <tr>
      <th>252</th>
      <td>253</td>
      <td>0</td>
      <td>1</td>
      <td>Stead, Mr. ...</td>
      <td>male</td>
      <td>62.0</td>
      <td>0</td>
      <td>0</td>
      <td>113514</td>
      <td>26.5500</td>
      <td>C87</td>
      <td>S</td>
    </tr>
    <tr>
      <th>275</th>
      <td>276</td>
      <td>1</td>
      <td>1</td>
      <td>Andrews, Mi...</td>
      <td>female</td>
      <td>63.0</td>
      <td>1</td>
      <td>0</td>
      <td>13502</td>
      <td>77.9583</td>
      <td>D7</td>
      <td>S</td>
    </tr>
    <tr>
      <th>280</th>
      <td>281</td>
      <td>0</td>
      <td>3</td>
      <td>Duane, Mr. ...</td>
      <td>male</td>
      <td>65.0</td>
      <td>0</td>
      <td>0</td>
      <td>336439</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
    </tr>
    <tr>
      <th>326</th>
      <td>327</td>
      <td>0</td>
      <td>3</td>
      <td>Nysveen, Mr...</td>
      <td>male</td>
      <td>61.0</td>
      <td>0</td>
      <td>0</td>
      <td>345364</td>
      <td>6.2375</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>438</th>
      <td>439</td>
      <td>0</td>
      <td>1</td>
      <td>Fortune, Mr...</td>
      <td>male</td>
      <td>64.0</td>
      <td>1</td>
      <td>4</td>
      <td>19950</td>
      <td>263.0000</td>
      <td>C23 C25 C27</td>
      <td>S</td>
    </tr>
    <tr>
      <th>456</th>
      <td>457</td>
      <td>0</td>
      <td>1</td>
      <td>Millet, Mr....</td>
      <td>male</td>
      <td>65.0</td>
      <td>0</td>
      <td>0</td>
      <td>13509</td>
      <td>26.5500</td>
      <td>E38</td>
      <td>S</td>
    </tr>
    <tr>
      <th>483</th>
      <td>484</td>
      <td>1</td>
      <td>3</td>
      <td>Turkula, Mr...</td>
      <td>female</td>
      <td>63.0</td>
      <td>0</td>
      <td>0</td>
      <td>4134</td>
      <td>9.5875</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>493</th>
      <td>494</td>
      <td>0</td>
      <td>1</td>
      <td>Artagaveyti...</td>
      <td>male</td>
      <td>71.0</td>
      <td>0</td>
      <td>0</td>
      <td>PC 17609</td>
      <td>49.5042</td>
      <td>NaN</td>
      <td>C</td>
    </tr>
    <tr>
      <th>545</th>
      <td>546</td>
      <td>0</td>
      <td>1</td>
      <td>Nicholson, ...</td>
      <td>male</td>
      <td>64.0</td>
      <td>0</td>
      <td>0</td>
      <td>693</td>
      <td>26.0000</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>555</th>
      <td>556</td>
      <td>0</td>
      <td>1</td>
      <td>Wright, Mr....</td>
      <td>male</td>
      <td>62.0</td>
      <td>0</td>
      <td>0</td>
      <td>113807</td>
      <td>26.5500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>570</th>
      <td>571</td>
      <td>1</td>
      <td>2</td>
      <td>Harris, Mr....</td>
      <td>male</td>
      <td>62.0</td>
      <td>0</td>
      <td>0</td>
      <td>S.W./PP 752</td>
      <td>10.5000</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>625</th>
      <td>626</td>
      <td>0</td>
      <td>1</td>
      <td>Sutton, Mr....</td>
      <td>male</td>
      <td>61.0</td>
      <td>0</td>
      <td>0</td>
      <td>36963</td>
      <td>32.3208</td>
      <td>D50</td>
      <td>S</td>
    </tr>
    <tr>
      <th>630</th>
      <td>631</td>
      <td>1</td>
      <td>1</td>
      <td>Barkworth, ...</td>
      <td>male</td>
      <td>80.0</td>
      <td>0</td>
      <td>0</td>
      <td>27042</td>
      <td>30.0000</td>
      <td>A23</td>
      <td>S</td>
    </tr>
    <tr>
      <th>672</th>
      <td>673</td>
      <td>0</td>
      <td>2</td>
      <td>Mitchell, M...</td>
      <td>male</td>
      <td>70.0</td>
      <td>0</td>
      <td>0</td>
      <td>C.A. 24580</td>
      <td>10.5000</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>745</th>
      <td>746</td>
      <td>0</td>
      <td>1</td>
      <td>Crosby, Cap...</td>
      <td>male</td>
      <td>70.0</td>
      <td>1</td>
      <td>1</td>
      <td>WE/P 5735</td>
      <td>71.0000</td>
      <td>B22</td>
      <td>S</td>
    </tr>
    <tr>
      <th>829</th>
      <td>830</td>
      <td>1</td>
      <td>1</td>
      <td>Stone, Mrs....</td>
      <td>female</td>
      <td>62.0</td>
      <td>0</td>
      <td>0</td>
      <td>113572</td>
      <td>80.0000</td>
      <td>B28</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>851</th>
      <td>852</td>
      <td>0</td>
      <td>3</td>
      <td>Svensson, M...</td>
      <td>male</td>
      <td>74.0</td>
      <td>0</td>
      <td>0</td>
      <td>347060</td>
      <td>7.7750</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>

</div>



<br>

- 반환된 `titanic_boolean` 객체가 DataFrame 이므로 뒤에 `[]` 연산자를 사용하여 특정 컬럼 추출 가능


```python
titanic_df[titanic_df['Age'] > 60][['Name', 'Age']].head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>33</th>
      <td>Wheadon, Mr...</td>
      <td>66.0</td>
    </tr>
    <tr>
      <th>54</th>
      <td>Ostby, Mr. ...</td>
      <td>65.0</td>
    </tr>
    <tr>
      <th>96</th>
      <td>Goldschmidt...</td>
      <td>71.0</td>
    </tr>
  </tbody>
</table>
</div>



<BR>

- `loc[]` 에도 동일하게 적용 (`['Name', 'Age']`는 컬럼 위치에 있어야 한다.)


```python
titanic_df.loc[titanic_df['Age'] > 60, ['Name', 'Age']].head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>33</th>
      <td>Wheadon, Mr...</td>
      <td>66.0</td>
    </tr>
    <tr>
      <th>54</th>
      <td>Ostby, Mr. ...</td>
      <td>65.0</td>
    </tr>
    <tr>
      <th>96</th>
      <td>Goldschmidt...</td>
      <td>71.0</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.6.6.1 복합 조건

- and 조건 : `&`
- or 조건 : `|`
- Not 조건 : `~`


```python
titanic_df[ (titanic_df['Age'] > 60) & (titanic_df['Pclass'] == 1) & (titanic_df['Sex'] == 'female')]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>275</th>
      <td>276</td>
      <td>1</td>
      <td>1</td>
      <td>Andrews, Mi...</td>
      <td>female</td>
      <td>63.0</td>
      <td>1</td>
      <td>0</td>
      <td>13502</td>
      <td>77.9583</td>
      <td>D7</td>
      <td>S</td>
    </tr>
    <tr>
      <th>829</th>
      <td>830</td>
      <td>1</td>
      <td>1</td>
      <td>Stone, Mrs....</td>
      <td>female</td>
      <td>62.0</td>
      <td>0</td>
      <td>0</td>
      <td>113572</td>
      <td>80.0000</td>
      <td>B28</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
cond1 = titanic_df['Age'] > 60
cond2 = titanic_df['Pclass'] == 1
cond3 = titanic_df['Sex'] == 'female'

titanic_df[cond1 & cond2 & cond3]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>275</th>
      <td>276</td>
      <td>1</td>
      <td>1</td>
      <td>Andrews, Mi...</td>
      <td>female</td>
      <td>63.0</td>
      <td>1</td>
      <td>0</td>
      <td>13502</td>
      <td>77.9583</td>
      <td>D7</td>
      <td>S</td>
    </tr>
    <tr>
      <th>829</th>
      <td>830</td>
      <td>1</td>
      <td>1</td>
      <td>Stone, Mrs....</td>
      <td>female</td>
      <td>62.0</td>
      <td>0</td>
      <td>0</td>
      <td>113572</td>
      <td>80.0000</td>
      <td>B28</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



<br>

## 4.7 정렬, Aggregation 함수, GroupBy 적용

### 4.7.1 DataFrame, Series의 정렬 - `sort_values()`

`DataFrame.sort_values(by, ascending=True, inplace=False)`

- `by`
  - 특정 컬럼을 기준으로 정렬 수행
  - 컬럼명 리스트를 할당  

- `ascending`
  - `ascending=True` : 오름차순 정렬 (default)
  - `ascending=False` : 내림차순 정렬  

- `inplace`
  - `inplace=False` : 호출한 DataFrame은 정렬되지 않은 채 정렬된 DataFrame 반환 (default)
  - `inplace=True` : 호출한 DataFrame의 정렬 결과를 그대로 적용


```python
titanic_sorted = titanic_df.sort_values(by=['Name'])
titanic_sorted.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>845</th>
      <td>846</td>
      <td>0</td>
      <td>3</td>
      <td>Abbing, Mr....</td>
      <td>male</td>
      <td>42.0</td>
      <td>0</td>
      <td>0</td>
      <td>C.A. 5547</td>
      <td>7.55</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>746</th>
      <td>747</td>
      <td>0</td>
      <td>3</td>
      <td>Abbott, Mr....</td>
      <td>male</td>
      <td>16.0</td>
      <td>1</td>
      <td>1</td>
      <td>C.A. 2673</td>
      <td>20.25</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>279</th>
      <td>280</td>
      <td>1</td>
      <td>3</td>
      <td>Abbott, Mrs...</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>1</td>
      <td>C.A. 2673</td>
      <td>20.25</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>



<br>


```python
titanic_sorted = titanic_df.sort_values(by=['Pclass', 'Name'], ascending=False)
titanic_sorted.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>868</th>
      <td>869</td>
      <td>0</td>
      <td>3</td>
      <td>van Melkebe...</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>345777</td>
      <td>9.5</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>153</th>
      <td>154</td>
      <td>0</td>
      <td>3</td>
      <td>van Billiar...</td>
      <td>male</td>
      <td>40.5</td>
      <td>0</td>
      <td>2</td>
      <td>A/5. 851</td>
      <td>14.5</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>282</th>
      <td>283</td>
      <td>0</td>
      <td>3</td>
      <td>de Pelsmaek...</td>
      <td>male</td>
      <td>16.0</td>
      <td>0</td>
      <td>0</td>
      <td>345778</td>
      <td>9.5</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>



<br>

### 4.7.2 Aggregation 함수 적용

- 집계 함수의 종류
  - `min()`
  - `max()`
  - `sum()`
  - `count()`

<br>

#### 4.7.2.1 DataFrame에 aggregation 사용

- DataFrame에서 바로 aggregation 함수를 호출할 경우 모든 컬럼에 aggregation을 적용한다.


```python
titanic_df.count()
```




    PassengerId    891
    Survived       891
    Pclass         891
    Name           891
    Sex            891
    Age            714
    SibSp          891
    Parch          891
    Ticket         891
    Fare           891
    Cabin          204
    Embarked       889
    dtype: int64



<br>

#### 4.7.2.2 컬럼에 aggregation 사용

- 특정 컬럼에 aggregation 함수 적용


```python
titanic_df[['Age', 'Fare']].mean()
```




    Age     29.699118
    Fare    32.204208
    dtype: float64



<br>

### 4.7.3 `groupby()` 적용

#### 4.7.3.1 `DataFrame.groupby(by)`  

- `by`에 groupby 대상 컬럼 지정
- DataFrame에 `groupby()`를 호출하면 `DataFrameGroupBy` 라는 또 다른 형태의 DataFrame을 반환


```python
titanic_groupby = titanic_df.groupby(by='Pclass')
print(type(titanic_groupby))
```

    <class 'pandas.core.groupby.generic.DataFrameGroupBy'>


<br>

#### 4.7.3.2 `DataFrame.groupby().aggregation함수`

- `groupby()` 대상 컬럼을 제외한 모든 컬럼에 해당 aggregation 함수를 적용


```python
titanic_groupby = titanic_df.groupby('Pclass').count()
titanic_groupby
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
    <tr>
      <th>Pclass</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>216</td>
      <td>216</td>
      <td>216</td>
      <td>216</td>
      <td>186</td>
      <td>216</td>
      <td>216</td>
      <td>216</td>
      <td>216</td>
      <td>176</td>
      <td>214</td>
    </tr>
    <tr>
      <th>2</th>
      <td>184</td>
      <td>184</td>
      <td>184</td>
      <td>184</td>
      <td>173</td>
      <td>184</td>
      <td>184</td>
      <td>184</td>
      <td>184</td>
      <td>16</td>
      <td>184</td>
    </tr>
    <tr>
      <th>3</th>
      <td>491</td>
      <td>491</td>
      <td>491</td>
      <td>491</td>
      <td>355</td>
      <td>491</td>
      <td>491</td>
      <td>491</td>
      <td>491</td>
      <td>12</td>
      <td>491</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.7.3.3 특정 컬럼 필터링

`DataFrameGroupBy` 객체에 `[['PassengerId','Survived']]`로 필터링 해 특정 컬럼에 대해 집계함수 적용


```python
titanic_groupby = titanic_df.groupby('Pclass')[['PassengerId','Survived']].count()
titanic_groupby
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
    </tr>
    <tr>
      <th>Pclass</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>216</td>
      <td>216</td>
    </tr>
    <tr>
      <th>2</th>
      <td>184</td>
      <td>184</td>
    </tr>
    <tr>
      <th>3</th>
      <td>491</td>
      <td>491</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.7.3.4 컬럼별 서로 다른 집계 함수 사용

특정 컬럼에 대해 서로 다른 집계 함수 사용 시 `agg()` 함수 안에 리스트 형태로 집계 함수를 할당


```python
titanic_df.groupby('Pclass')['Age'].agg([max, min])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>max</th>
      <th>min</th>
    </tr>
    <tr>
      <th>Pclass</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>80.0</td>
      <td>0.92</td>
    </tr>
    <tr>
      <th>2</th>
      <td>70.0</td>
      <td>0.67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>74.0</td>
      <td>0.42</td>
    </tr>
  </tbody>
</table>
</div>



<br>

서로 다른 컬럼들에 대해 서로 다른 집계 함수 사용 시 딕셔너리 형태로 집계가 적용될 컬럼들과 집계 함수를 입력


```python
agg_format = {'Age': 'max', 'SibSp': 'sum', 'Fare': 'mean'}
titanic_df.groupby('Pclass').agg(agg_format)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Fare</th>
    </tr>
    <tr>
      <th>Pclass</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>80.0</td>
      <td>90</td>
      <td>84.154687</td>
    </tr>
    <tr>
      <th>2</th>
      <td>70.0</td>
      <td>74</td>
      <td>20.662183</td>
    </tr>
    <tr>
      <th>3</th>
      <td>74.0</td>
      <td>302</td>
      <td>13.675550</td>
    </tr>
  </tbody>
</table>
</div>



<br>

## 4.8 결손 데이터 처리하기

결손 데이터

- 컬럼에 값이 없다. (NULL인 경우)
- 넘파이는 NaN으로 표시
- NaN 값은 평균, 총합 등의 함수 연산 시 제외됨  
(특정 컬럼의 100개 데이터 중 10개가 NaN 값일 경우, 이 컬럼의 평균 값은 90개 데이터에 대한 평균)

<br>

### 4.8.1 `isna()`로 결손 데이터 여부 확인

#### 4.8.1.1 `DataFrame.isna()`

- NaN 여부를 확인하는 API
- DataFrame에 `isna()` 함수를 적용하면 모든 컬럼의 값이 NaN인지 아닌지 `True`나 `False`로 알려줌


```python
titanic_df.isna().head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.8.1.2 `DataFrame.isna().sum()`

- 컬럼별 결손 데이터 갯수 확인
- `sum()` 함수 사용 시 True는 1로, False는 0으로 변환됨


```python
titanic_df.isna().sum()
```




    PassengerId      0
    Survived         0
    Pclass           0
    Name             0
    Sex              0
    Age            177
    SibSp            0
    Parch            0
    Ticket           0
    Fare             0
    Cabin          687
    Embarked         2
    dtype: int64



<br>

### 4.8.2 `fillna()`로 결손 데이터 처리하기

#### 4.8.2.1 `DataFrame.fillna()`

- NaN 값을 다른 값으로 대체


```python
# Cabin 컬럼의 NaN값을 'C000'으로 대체
titanic_df['Cabin'] = titanic_df['Cabin'].fillna('C000')
titanic_df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr....</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>C000</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mr...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, ...</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 31...</td>
      <td>7.9250</td>
      <td>C000</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.8.2.2 `DataFrame.fillna(inplace)`

- `inplace=False` 사용 시 결과를 다시 해당 컬럼에 할당해 줘야 함
- `inplace=True` 사용 시 할당할 필요 없이 바로 호출한 DataFrame에 `fillna()` 함수 결과 적용됨


```python
# Age 컬럼의 NaN값을 Age 컬럼의 평균값으로 대체
titanic_df['Age'] = titanic_df['Age'].fillna(titanic_df['Age'].mean())

# Embarked 컬럼의 NaN값을 'S'로 대체
titanic_df['Embarked'] = titanic_df['Embarked'].fillna('S')

titanic_df.isna().sum()
```




    PassengerId    0
    Survived       0
    Pclass         0
    Name           0
    Sex            0
    Age            0
    SibSp          0
    Parch          0
    Ticket         0
    Fare           0
    Cabin          0
    Embarked       0
    dtype: int64



<br>

## 4.9 `apply` `lambda` 식으로 데이터 가공

### 4.9.1 `lamdba` 식

#### 4.9.1.1 `get_square(a)` 함수

- 입력값의 제곱 값을 구해서 반환


```python
def get_square(a) :
    return a**2

print('3의 제곱은 : ', get_square(3))
```

    3의 제곱은 :  9


<br>

#### 4.9.1.2 `lambda` 식 사용

`get_square()` 함수를 정의하는 것보다 `lambda` 식을 사용하여 더 간편하게 표현할 수 있다.


```python
lambda_square = lambda x : x**2
print('3의 제곱은 : ', lambda_square(3))
```

    3의 제곱은 :  9


<br>

#### 4.9.1.3 `lambda` 입력인자

- 반환될 입력 인자의 계산식(반환값)`
- 여러 개의 값을 입력 인자로 사용해야 할 경우에는 보통 `map()` 함수를 결합해서 사용


```python
a = [1,2,3]
squares = map(lambda x : x**2, a)
list(squares)
```




    [1, 4, 9]



<br>

#### 4.9.1.4 `Series.apply(lambda 식)`


```python
# Name_len : Name 컬럼의 문자열 개수
titanic_df['Name_len'] = titanic_df['Name'].apply(lambda x : len(x))
titanic_df[['Name', 'Name_len']].head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Name_len</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Braund, Mr....</td>
      <td>23</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cumings, Mr...</td>
      <td>51</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Heikkinen, ...</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.9.1.5 `lambda` 식에 `if else` 절 사용


```python
# Child_Adult : 나이가 15세 미만이면 'Child', 그렇지 않으면 'Adult'로 구분
titanic_df['Child_Adult'] = titanic_df['Age'].apply(lambda x : 'Child' if x <= 15 else 'Adult')
titanic_df[['Age', 'Child_Adult']].head(8)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Child_Adult</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>22.000000</td>
      <td>Adult</td>
    </tr>
    <tr>
      <th>1</th>
      <td>38.000000</td>
      <td>Adult</td>
    </tr>
    <tr>
      <th>2</th>
      <td>26.000000</td>
      <td>Adult</td>
    </tr>
    <tr>
      <th>3</th>
      <td>35.000000</td>
      <td>Adult</td>
    </tr>
    <tr>
      <th>4</th>
      <td>35.000000</td>
      <td>Adult</td>
    </tr>
    <tr>
      <th>5</th>
      <td>29.699118</td>
      <td>Adult</td>
    </tr>
    <tr>
      <th>6</th>
      <td>54.000000</td>
      <td>Adult</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2.000000</td>
      <td>Child</td>
    </tr>
  </tbody>
</table>
</div>



<br>

#### 4.9.1.6 `lambda`식 `if else`절의 올바른 사용

`lambda x : if x <= 15 'Child' else 'Adult'` : (x)  
`lambda x : 'Child' if x <= 15 else 'Adult'` : (o)  


`lambda` 식 `:` 기호의 오른편에 반환 값이 있어야 한다.  
`else`의 경우에는 `else` 식이 먼저 나오고 반환 값이 나중에 나오면 된다.

<br>

#### 4.9.1.7 `if else`절 중복 사용

`lambda` 식은 `if, else if, else` 는 지원하지 않음.  
`else` 절을 `()`로 내포해 `()` 내에서 다시 `if else`를 적용해서 사용


```python
# Age_cat : 나이가 15세 이하이면 'Child', 15 ~ 60세 사이는 'Adult', 61세 이상은 'Elderly'로 분류
titanic_df['Age_cat'] = titanic_df['Age'].apply(lambda x : 'Child' if x <= 15 else ('Adult' if x <= 60 else 'Elderly'))
titanic_df['Age_cat'].value_counts()
```




    Adult      786
    Child       83
    Elderly     22
    Name: Age_cat, dtype: int64



<br>

#### 4.9.1.8 `lambda`식에 사용자 정의 함수 사용

조건이 복잡한 경우에는 별도의 함수를 만들어서 `lambda` 식의 반환값으로 지정


```python
# 나이에 따라 세분화된 분류를 수행하는 함수 생성
def get_category(age) :
    cat = ''

    if age <= 5 : cat = 'Baby'
    elif age <= 12 : cat = 'Child'
    elif age <= 18 : cat = 'Teenager'
    elif age <= 25 : cat = 'Student'
    elif age <= 35 : cat = 'Young Adult'
    elif age <= 60 : cat = 'Adult'
    else : cat = 'Elderly'

    return cat
```


```python
# lambda 식에 위에서 생성한 get category() 함수를 반환값으로 지정
# get_category(X)는 입력값으로 'Age' 컬럼 값을 받아서 해당하는 cat 반환
titanic_df['Age_cat'] = titanic_df['Age'].apply(lambda x : get_category(x))
titanic_df[['Age', 'Age_cat']].head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Age_cat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>22.0</td>
      <td>Student</td>
    </tr>
    <tr>
      <th>1</th>
      <td>38.0</td>
      <td>Adult</td>
    </tr>
    <tr>
      <th>2</th>
      <td>26.0</td>
      <td>Young Adult</td>
    </tr>
    <tr>
      <th>3</th>
      <td>35.0</td>
      <td>Young Adult</td>
    </tr>
    <tr>
      <th>4</th>
      <td>35.0</td>
      <td>Young Adult</td>
    </tr>
  </tbody>
</table>
</div>
