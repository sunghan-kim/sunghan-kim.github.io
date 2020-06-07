---
title: "정렬 알고리즘 (Sort Algorithm)"
permalink: /sort-algorithm/
sidebar:
  nav: sidebar-algorithm-sort-algorithm
author_profile: false
header:
  overlay_image: /assets/images/development.jpg
  overlay_filter: 0.5
---

# 정렬 알고리즘별 특징 정리

<img src="/assets/images/algorithm/sort-algorithm/sort-algorithm-summary.jpg" />

<br>

# 정렬 알고리즘별 파이썬 코드 구현

## 버블 정렬(Bubble Sort) 구현

```python
def bubblesort(data):
    for index in range(len(data) - 1):
        swap = False
        for index2 in range(len(data) - index - 1):
            if data[index2] > data[index2 + 1]:
                data[index2], data[index2 + 1] = data[index2 + 1], data[index2]
                swap = True

        if swap == False:
            break
    return data
```

## 삽입 정렬(Insertion Sort) 구현

```python
def insertion_sort(data):
    for index in range(len(data) - 1):
        for index2 in range(index+1, 0, -1):
            if data[index2] < data[index2 - 1]:
                data[index2], data[index2 - 1] = data[index2 - 1], data[index2]
            else:
                break
    return data
```

## 선택 정렬(Selection Sort) 구현

```python
def selection_sort(data):
    for stand in range(len(data) - 1):
        lowest = stand
        for index in range(stand+1, len(data)):
            if data[lowest] > data[index]:
                lowest = index
        data[stand], data[lowest] = data[lowest], data[stand]
    return data
```

## 병합 정렬(Merge Sort) 구현

```python
def merge(left, right):
    merged = list()
    left_index, right_index = 0, 0

    while len(left) > left_index and len(right) > right_index:
        if left[left_index] > right[right_index]:
            merged.append(right[right_index])
            right_index += 1
        else:
            merged.append(left[left_index])
            left_index += 1

    while len(left) > left_index:
        merged.append(left[left_index])
        left_index += 1

    while len(right) > right_index:
        merged.append(right[right_index])
        right_index += 1

    return merged

def mergesplit(data):
    if len(data) <= 1:
        return data
    medium = int(len(data)/2)
    left = data[:medium]
    right = data[medium:]
    return merge(mergesplit(left), mergesplit(right))
```

## 퀵 정렬(Quick Sort) 구현

```python
def quick_sort(data):
    if len(data) <= 1:
        return data
    pivot = data[0]
    left = [item for item in data[1:] if item < pivot]
    right = [item for item in data[1:] if item > pivot]
    return quick_sort(left) + [pivot] + quick_sort(right)
```
