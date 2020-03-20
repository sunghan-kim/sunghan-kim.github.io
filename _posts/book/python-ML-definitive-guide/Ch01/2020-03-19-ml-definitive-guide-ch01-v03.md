---
title: "1.3 넘파이"
date: 2020-03-19
category:
  - Python
tag :
  - NumPy
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

# v03. 넘파이

<br>

## 3.1 넘파이 ndarray 개요


```python
import numpy as np
```

<br>

넘파이의 기반 데이터 타입은 `ndarray`이다.  
`ndarray.shape` : array의 크기(행과 열의 수) 확인


```python
array1 = np.array([1,2,3])
print('array1 type:', type(array1))
print('array1 array 형태:', array1.shape)
```
```
array1 type: <class 'numpy.ndarray'>
array1 array 형태: (3,)
```

<br>

```python
array2 = np.array([[1,2,3],
                   [2,3,4]])
print('array2 type:', type(array2))
print('array2 array 형태:', array2.shape)
```
```
array2 type: <class 'numpy.ndarray'>
array2 array 형태: (2, 3)
```

<br>

```python
array3 = np.array([[1,2,3]])
print('array3 type:', type(array3))
print('array3 array 형태:', array3.shape)
```
```
array3 type: <class 'numpy.ndarray'>
array3 array 형태: (1, 3)
```

<br>

`ndarray.ndim` : array의 차원 확인


```python
print('array1: {:0}차원, array2: {:1}차원, array3: {:2}차원'.format(array1.ndim,
                                                                   array2.ndim,
                                                                   array3.ndim))
```

    array1: 1차원, array2: 2차원, array3:  2차원


<br>

## 3.2 ndarray의 데이터 타입

`dtype` : ndarray 내의 데이터 타입 확인


```python
list1 = [1,2,3]
print(type(list1))

array1 = np.array(list1)
print(type(array1))
print(array1, array1.dtype)
```

    <class 'list'>
    <class 'numpy.ndarray'>
    [1 2 3] int32


<br>

int형과 string형이 섞여 있는 경우


```python
list2 = [1,2, 'test']
array2 = np.array(list2)
print(array2, array2.dtype)
```

    ['1' '2' 'test'] <U11


<br>

int형과 float형이 섞여 있는 경우


```python
list3 = [1,2, 3.0]
array3 = np.array(list3)
print(array3, array3.dtype)
```

    [1. 2. 3.] float64


<br>

`astype()` : ndarray 내 데이터값의 타입 변경

- int32형 $$\rightarrow$$ float64으로 변환


```python
array_int = np.array([1,2,3])
print("array_int dtype : ", array_int.dtype)

array_float = array_int.astype('float64')
print(array_float, array_float.dtype)
```

    array_int dtype :  int32
    [1. 2. 3.] float64

<br>

- float64 $$\rightarrow$$ int32로 변환 (소숫점 아래 데이터 없는 경우)


```python
array_int1 = array_float.astype('int32')
print(array_int1, array_int1.dtype)
```

    [1 2 3] int32

<br>

- float64 $$\rightarrow$$ int32로 변환 (소숫점 아래 데이터 있는 경우)


```python
array_float1 = np.array([1.1, 2.1, 3.1])
print(array_float1, array_float1.dtype)

array_int2 = array_float1.astype('int32')
print(array_int2, array_int2.dtype)
```

    [1.1 2.1 3.1] float64
    [1 2 3] int32


<br>

## 3.3 ndarray를 편리하게 생성하기 - `arange`, `zeros`, `ones`

### 3.3.1 `arange()`


```python
sequence_array = np.arange(10)
print(sequence_array)
print(sequence_array.dtype, sequence_array.shape)
```

    [0 1 2 3 4 5 6 7 8 9]
    int32 (10,)


<br>

### 3.3.2 `zeros()`


```python
zero_array = np.zeros((3,2), dtype='int32')
print(zero_array)
print(zero_array.dtype, zero_array.shape)
```

    [[0 0]
     [0 0]
     [0 0]]
    int32 (3, 2)


<br>

### 3.3.3 `ones()`


```python
one_array = np.ones((3,2))
print(one_array)
print(one_array.dtype, one_array.shape)
```

    [[1. 1.]
     [1. 1.]
     [1. 1.]]
    float64 (3, 2)


<br>

## 3.4 `ndarray`의 차원과 크기를 변경하는 `reshape()`


```python
array1 = np.arange(10)
print('array1:\n', array1)

array2 = array1.reshape(2,5)
print('array2:\n', array2)

array3 = array1.reshape(5,2)
print('array3:\n', array3)
```

    array1:
     [0 1 2 3 4 5 6 7 8 9]
    array2:
     [[0 1 2 3 4]
     [5 6 7 8 9]]
    array3:
     [[0 1]
     [2 3]
     [4 5]
     [6 7]
     [8 9]]



```python
# array1.reshape(4,3)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-23-a40469ec5825> in <module>
    ----> 1 array1.reshape(4,3)


    ValueError: cannot reshape array of size 10 into shape (4,3)


<br>

`reshape()`에 -1을 인자로 사용


```python
array1 = np.arange(10)
print(array1)

array2 = array1.reshape(-1, 5)
print('array2 shape: ', array2.shape)

array3 = array1.reshape(5, -1)
print('array3 shape: ', array3.shape)
```

    [0 1 2 3 4 5 6 7 8 9]
    array2 shape:  (2, 5)
    array3 shape:  (5, 2)

<br>

```python
array1 = np.arange(10)
# array4 = array1.reshape(-1, 4)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-26-474c3d9b15cb> in <module>
          1 array1 = np.arange(10)
    ----> 2 array4 = array1.reshape(-1, 4)


    ValueError: cannot reshape array of size 10 into shape (4)


<br>

`reshape(-1, 1)`

- 원본 ndarray가 어떤 형태라도 2차원이고, 여러 개의 로우를 가지되 반드시 1개의 컬럼을 가진 ndarray로 변환됨을 보장

<br>

`tolist()`

- ndarray를 list 자료형으로 변환


```python
array1 = np.arange(8)
array3d = array1.reshape(2, 2, 2)
print('array3d:\n', array3d.tolist())

# 3차원 ndarray를 2차원 ndarray로 변환
array5 = array3d.reshape(-1, 1)
print('array5:\n', array5.tolist())
print('array5 shap: ', array5.shape)

# 1차원 ndarray를 2차원 ndarray로 변환
array6 = array1.reshape(-1, 1)
print('array6:\n', array6.tolist())
print('array6 shape: ', array6.shape)
```

    array3d:
     [[[0, 1], [2, 3]], [[4, 5], [6, 7]]]
    array5:
     [[0], [1], [2], [3], [4], [5], [6], [7]]
    array5 shap:  (8, 1)
    array6:
     [[0], [1], [2], [3], [4], [5], [6], [7]]
    array6 shape:  (8, 1)


<br>

## 3.5 넘파이의 ndarray의 데이터 세트 선택하기 - 인덱싱(Indexing)

### 3.5.1 단일 값 추출 (특정한 데이터만 추출)


```python
# 1부터 9까지의 1차원 ndarray 생성
array1 = np.arange(start=1, stop=10)
print('array1:', array1)

# index는 0부터 시작하므로 array1[2]는 3번째 index 위치의 데이터값을 의미
value = array1[2]
print('value: ', value)
print(type(value))
```

    array1: [1 2 3 4 5 6 7 8 9]
    value:  3
    <class 'numpy.int32'>

<br>

- `[-1]`는 맨 뒤의 데이터값 의미


```python
print('맨 뒤의 값:', array1[-1], ' 맨 뒤에서 두 번째 값:', array1[-2])
```

    맨 뒤의 값: 9  맨 뒤에서 두 번째 값: 8

<br>

- 단일 인덱스 이용 ndarray 내의 데이터값 수정


```python
array1[0] = 9
array1[8] = 0
print('array1:', array1)
```

    array1: [9 2 3 4 5 6 7 8 0]


<br>

다차원 ndarray에서 단일 값 추출


```python
array1d = np.arange(start=1, stop=10)
array2d = array1d.reshape(3, 3)
print(array2d)

print('(row=0, col=0) index 가리키는 값 : ', array2d[0, 0])
print('(row=0, col=1) index 가리키는 값 : ', array2d[0, 1])
print('(row=1, col=0) index 가리키는 값 : ', array2d[1, 0])
print('(row=2, col=2) index 가리키는 값 : ', array2d[2, 2])
```

    [[1 2 3]
     [4 5 6]
     [7 8 9]]
    (row=0, col=0) index 가리키는 값 :  1
    (row=0, col=1) index 가리키는 값 :  2
    (row=1, col=0) index 가리키는 값 :  4
    (row=2, col=2) index 가리키는 값 :  9


<br>

`axis`

- `axis=0` : 로우 방향의 축 의미
- `axis=1` : 컬럼 방향의 축 의미
- [row=0, col=1] $$\Rightarrow$$ [axis 0=0, axis 1=1]
- 2차원 $$\Rightarrow$$ axis 0, axis 1
- 3차원 $$\Rightarrow$$ axis 0, axis 1, axis 2
- 축 기반의 연산에서 axis가 생략 $$\Rightarrow$$ axis 0을 의미

<br>

### 3.5.2 슬라이싱


```python
array1 = np.arange(start=1, stop=10)
array3 = array1[0:3]
print(array3)
print(type(array3))
```

    [1 2 3]
    <class 'numpy.ndarray'>

<br>

```python
array1 = np.arange(start=1, stop=10)
array4 = array1[:3]
print(array4)

array5 = array1[3:]
print(array5)

array6 = array1[:]
print(array6)
```

    [1 2 3]
    [4 5 6 7 8 9]
    [1 2 3 4 5 6 7 8 9]

<br>

```python
array1d = np.arange(start=1, stop=10)
array2d = array1d.reshape(3, 3)
print('array2d:\n', array2d)

print('array2d[0:2, 0:2] \n', array2d[0:2, 0:2])
print('array2d[1:3, 0:3] \n', array2d[1:3, 0:3])
print('array2d[1:3, :] \n', array2d[1:3, :])
print('array2d[:, :] \n', array2d[:, :])
print('array2d[:2, 1:] \n', array2d[:2, 1:])
print('array2d[:2, 0] \n', array2d[:2, 0])
```

    array2d:
     [[1 2 3]
     [4 5 6]
     [7 8 9]]
    array2d[0:2, 0:2]
     [[1 2]
     [4 5]]
    array2d[1:3, 0:3]
     [[4 5 6]
     [7 8 9]]
    array2d[1:3, :]
     [[4 5 6]
     [7 8 9]]
    array2d[:, :]
     [[1 2 3]
     [4 5 6]
     [7 8 9]]
    array2d[:2, 1:]
     [[2 3]
     [5 6]]
    array2d[:2, 0]
     [1 4]

<br>

```python
print(array2d[0])
print(array2d[1])
print('array2d[0] shape : ', array2d[0].shape, '\narray2d[1] shape : ', array2d[1].shape)
```

    [1 2 3]
    [4 5 6]
    array2d[0] shape :  (3,)
    array2d[1] shape :  (3,)


<br>

### 3.5.3 팬시 인덱싱


```python
array1d = np.arange(start=1, stop=10)
array2d = array1d.reshape(3, 3)

array3 = array2d[[0, 1], 2] # (0, 2), (1, 2)
print('array2d[[0, 1], 2] => ', array3.tolist())

array4 = array2d[[0, 1], 0:2] # ( (0,0), (0,1) ), ( (1,0), (1,1) )
print('array2d[[0, 1], 0:2] => ', array4.tolist())

array5 = array2d[[0, 1]] # ( (0, :), (1, :) )
print('array2d[[0, 1]] => ', array5.tolist())
```

    array2d[[0, 1], 2] =>  [3, 6]
    array2d[[0, 1], 0:2] =>  [[1, 2], [4, 5]]
    array2d[[0, 1]] =>  [[1, 2, 3], [4, 5, 6]]


<br>

### 3.5.4 불린 인덱싱


```python
array1 = np.arange(start=1, stop=10)

# [] 안에 array1d > 5 Boolean indexing을 적용
array3 = array1d[array1d > 5]
print('array1d > 5 불린 인덱싱 결과 값 : ', array3)
```

    array1d > 5 불린 인덱싱 결과 값 :  [6 7 8 9]

<br>

```python
array1d > 5
```


    array([False, False, False, False, False,  True,  True,  True,  True])

<br>


```python
type(array1d > 5)
```


    numpy.ndarray

<br>


```python
boolean_indexes = np.array([False, False, False, False, False,  True,  True,  True,  True])
array3 = array1d[boolean_indexes]
print('불린 인덱스로 필터링 결과 : ', array3)
```

    불린 인덱스로 필터링 결과 :  [6 7 8 9]

<br>

```python
indexes = np.array([5,6,7,8])
array4 = array1d[indexes]
print('일반 인덱스로 필터링 결과 : ', array4)
```

    일반 인덱스로 필터링 결과 :  [6 7 8 9]


<br>

## 3.6 행렬의 정렬 - `sort()`와 `argsort()`

넘파이에서의 행렬을 정렬하는 대표적인 방법

- `np.sort()`
- `ndarray.sort()`

<br>

`argsort()` : 정렬된 행렬의 인덱스 반환

<br>

### 3.6.1 행렬 정렬

`np.sort()`

- 원 행렬은 그대로 유지한 채 원 행렬의 정렬된 행렬 반환

`ndarray.sort()`

- 원 행렬 자체를 정렬한 형태로 변환
- 반환 값은 None


```python
org_array = np.array([3, 1, 9, 5])
print('원본 행렬 : ', org_array)

# np.sort()로 정렬
sort_array1 = np.sort(org_array)
print('np.sort() 호출 후 반환된 정렬 행렬 : ', sort_array1)
print('np.sort() 호출 후 원본 행렬 : ', org_array)

# ndarray.sort()로 정렬
sort_array2 = org_array.sort()
print('ndarray.sort() 호출 후 반환된 행렬 : ', sort_array2)
print('ndarray.sort() 호출 후 원본 행렬 : ', org_array)
```

    원본 행렬 :  [3 1 9 5]
    np.sort() 호출 후 반환된 정렬 행렬 :  [1 3 5 9]
    np.sort() 호출 후 원본 행렬 :  [3 1 9 5]
    ndarray.sort() 호출 후 반환된 행렬 :  None
    ndarray.sort() 호출 후 원본 행렬 :  [1 3 5 9]


<br>

`[::-1]` : 내림차순 정렬


```python
sort_array1_desc = np.sort(org_array)[::-1]
print('내림차순으로 정렬 : ', sort_array1_desc)
```

    내림차순으로 정렬 :  [9 5 3 1]


<br>

행렬이 2차원 이상일 경우에 `axis` 축 값 설정을 통해 로우 방향, 컬럼 방향으로 정렬 수행

- `axis=0` : 로우 방향
- `axis=1` : 컬럼 방향


```python
array2d = np.array([[8, 12],
                    [7, 1]])
print(array2d)

sort_array2d_axis0 = np.sort(array2d, axis=0)
print('로우 방향으로 정렬 : \n', sort_array2d_axis0)

sort_array2d_axis1 = np.sort(array2d, axis=1)
print('컬럼 방향으로 정렬 : \n', sort_array2d_axis1)
```

    [[ 8 12]
     [ 7  1]]
    로우 방향으로 정렬 :
     [[ 7  1]
     [ 8 12]]
    컬럼 방향으로 정렬 :
     [[ 8 12]
     [ 1  7]]


<br>

### 3.6.2 정렬된 행렬의 인덱스를 반환하기

원본 행렬이 정렬되었을 때 기존 원본 행렬의 원소에 대한 인덱스를 필요로 할 때 `np.argsort()`를 이용.  
`np.argsort()`는 정렬 행렬의 원본 행렬 인덱스를 `ndarray` 형으로 반환


```python
org_array = np.array([3, 1, 9, 5])
sort_indices = np.argsort(org_array)
print(type(sort_indices))
print('행렬 정렬 시 원본 행렬의 인덱스 : ', sort_indices)
```

    <class 'numpy.ndarray'>
    행렬 정렬 시 원본 행렬의 인덱스 :  [1 0 3 2]


<br>

내림차순 정렬 (`[::-1]`)


```python
org_array = np.array([3, 1, 9, 5])
sort_indices = np.argsort(org_array)[::-1]
print(type(sort_indices))
print('행렬 내림차순 정렬 시 원본 행렬의 인덱스 : ', sort_indices)
```

    <class 'numpy.ndarray'>
    행렬 내림차순 정렬 시 원본 행렬의 인덱스 :  [2 3 0 1]


<br>

## 3.7 선형대수 연산 - 행렬 내적과 전치 행렬 구하기

### 3.7.1 행렬 내적(행렬 곱)

`np.dot()`


```python
A = np.array([[1, 2, 3],
              [4, 5, 6]])
B = np.array([[7, 8],
              [9, 10],
              [11, 12]])

dot_product = np.dot(A, B)
print('행렬 내적 결과 : \n', dot_product)
```

    행렬 내적 결과 :
     [[ 58  64]
     [139 154]]


<br>

### 3.7.2 전치 행렬

`np.transpose()`


```python
A = np.array([[1, 2],
              [3, 4]])
transpose_mat = np.transpose(A)
print('A의 전치 행렬 : \n', transpose_mat)
```

    A의 전치 행렬 :
     [[1 3]
     [2 4]]
