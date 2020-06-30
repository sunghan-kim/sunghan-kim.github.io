---
title: "탐색 알고리즘 (Search Algorithm)"
permalink: /search-algorithm/
sidebar:
  nav: sidebar-algorithm-search-algorithm
author_profile: false
header:
  overlay_image: /assets/images/development.jpg
  overlay_filter: 0.5
---

# 탐색 알고리즘별 특징 정리

<img src="/assets/images/algorithm/search-algorithm/search-algorithm-summary.jpg" />

<br>

# 탐색 알고리즘 구현

## 순차 탐색 (Sequential Search) 구현

```python
def sequential(data_list, search_data):
    for index in range(len(data_list)):
        if data_list[index] == search_data:
            return index
    return -1
```

<br>

## 이진 탐색 (Binary Search) 구현

```python
def binary_search(data, search):
    print(data)
    if len(data) == 1 and search == data[0]:
        return True
    if len(data) == 1 and search != data[0]:
        return False
    if len(data) == 0:
        return False

    medium = len(data) // 2
    if search == data[medium]:
        return True
    else:
        if search > data[medium]:
            return binary_search(data[medium+1:], search)
        else:
            return binary_search(data[:medium], search)
```

<br>

## 그래프 표현 1

- BFS, DFS 구현 시 사용됨

<img src="/assets/images/algorithm/search-algorithm/graph.jpg" width="400px" />

```python
graph = dict()

graph['A'] = ['B', 'C']
graph['B'] = ['A', 'D']
graph['C'] = ['A', 'G', 'H', 'I']
graph['D'] = ['B', 'E', 'F']
graph['E'] = ['D']
graph['F'] = ['D']
graph['G'] = ['C']
graph['H'] = ['C']
graph['I'] = ['C', 'J']
graph['J'] = ['I']
```

<br>

## 너비 우선 탐색 (Breadth First Search, BFS) 구현

```python
def bfs(graph, start_node):
    need_visit, visited = list(), list()
    need_visit.append(start_node)
    while need_visit:
        node = need_visit.pop(0)
        if node not in visited:
            visited.append(node)
            need_visit.extend(graph[node])
    return visited
```

<br>

## 깊이 우선 탐색 (Depth First Search, DFS) 구현

```python
def dfs(graph, start_node):
    need_visit, visited = list(), list()
    need_visit.append(start_node)
    whlie need_visit:
        node = need_visit.pop()
        if node not in visited:
            visited.append(node)
            need_visit.extend(graph[node])
    return visited
```

<br>

# 최단 경로 탐색 알고리즘

## 다익스트라 알고리즘 (Dijkstra Algorithm) 구현

```python
mygraph = {
    'A': {'B': 8, 'C': 1, 'D': 2},
    'B': {},
    'C': {'B': 5, 'D': 2},
    'D': {'E': 3, 'F': 5},
    'E': {'F': 1},
    'F': {'A': 5}
}

import heapq

def dijkstra(graph, start):
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    queue = []
    heapq.heappush(queue, [distances[start], start]) # [0, start]

    while queue:
        current_distance, current_node = heapq.heappop(queue) # [0, start] pop

        if distances[current_node] < current_distance:
            continue

        for adjacent, weight in graph[current_node].items():
            distance = current_distance + weight

            if distance < distances[adjacent]:
                distances[adjacent] = distance
                heapq.heappush(queue, [distance, adjacent])

    return distances
```

<br>

# 최소 신장 트리(MST) 구현 알고리즘

## 그래프 표현 2

- 크루스칼 알고리즘, 프림 알고리즘 구현에 사용

<img src="/assets/images/algorithm/search-algorithm/graph2.jpg" width="300px" />

```python
mygraph = {
    'vertices': ['A', 'B', 'C', 'D', 'E', 'F', 'G'],
    'edges': [
        (7, 'A', 'B'),
        (5, 'A', 'D'),
        (7, 'B', 'A'),
        (8, 'B', 'C'),
        (9, 'B', 'D'),
        (7, 'B', 'E'),
        (8, 'C', 'B'),
        (5, 'C', 'E'),
        (5, 'D', 'A'),
        (9, 'D', 'B'),
        (7, 'D', 'E'),
        (6, 'D', 'F'),
        (7, 'E', 'B'),
        (5, 'E', 'C'),
        (7, 'E', 'D'),
        (8, 'E', 'F'),
        (9, 'E', 'G'),
        (6, 'F', 'D'),
        (8, 'F', 'E'),
        (11, 'F', 'G'),
        (9, 'G', 'E'),
        (11, 'G', 'F')
    ]
}
```

## 크루스칼 알고리즘(Kruskal's Algorithm) 구현

```python
parent = dict()
rank = dict()

def find(node):
    if parent[node] != node:
        parent[node] = find(parent[node])
    return parent[node]

def union(node_v, node_u):
    root1 = find(node_v)
    root2 = find(node_u)

    if rank[root1] > rank[root2]:
        parent[root2] = root1
    else:
        parent[root1] = root2
        if rank[root1] == rank[root2]:
            rank[root2] += 1

def make_set(node):
    parent[node] = node
    rank[node] = 0

def kruskal(graph):

    mst = list()

    for node in graph['vertices']:
        make_set(node)

    edges = graph['edges']
    edges.sort()

    for edge in edges:
        weight, node_v, node_u = edge

        if find(node_v) != find(node_u):
            union(node_v, node_u)
            mst.append(edge)

    return mst
```

<br>

## 프림 알고리즘(Prim's Algorithm) 구현

```python
myedges = [
    (7, 'A', 'B'), (5, 'A', 'D'),
    (8, 'B', 'C'), (9, 'B', 'D'), (7, 'B', 'E'),
    (5, 'C', 'E'),
    (7, 'D', 'E'), (6, 'D', 'F'),
    (8, 'E', 'F'), (9, 'E', 'G'),
    (11, 'F', 'G')
]

from collections import defaultdict
from heapq import *

def prim(start_node, edges):

    mst = list()
    adjacent_edges = defaultdict(list)

    for edge in edges:
        weight, n1, n2 = edge
        adjacent_edges[n1].append((weight, n1, n2))
        adjacent_edges[n2].append((weight, n2, n1))

    connected_nodes = set(start_node)
    candidate_edge_list = adjacent_edges[start_node]

    heapify(candidate_edge_list)

    while candidate_edge_list:
        weight, n1, n2 = heappop(candidate_edge_list)

        if n2 not in connected_nodes:
            connected_nodes.add(n2)
            mst.append((weight, n1, n2))

            for edge in adjacent_edges[n2]:
                if edge[2] not in connected_nodes:
                    heappush(candidate_edge_list, edge)

    return mst
```

<br>

## 개선된 프림 알고리즘(Advanced Prim's Algorithm) 구현

```python
mygraph = {
    'A': {'B': 7, 'D': 5},
    'B': {'A': 7, 'D': 9, 'C': 8, 'E': 7},
    'C': {'B': 8, 'E': 5},
    'D': {'A': 5, 'B': 9, 'E': 7, 'F': 6},
    'E': {'B': 7, 'C': 5, 'D': 7, 'F': 8, 'G': 9},
    'F': {'D': 6, 'E': 8, 'G': 11},
    'G': {'E': 9, 'F': 11}    
}

from heapdict import heapdict

def prim(graph, start):
    mst = list()
    keys = heapdict()
    pi = dict()
    total_weight = 0

    for node in graph.keys():
        keys[node] = float('inf')
        pi[node] = None

    keys[start] = 0
    pi[start] = start

    while keys:
        current_node, current_key = keys.popitem()
        mst.append([pi[current_node], current_node, current_key])
        total_weight += current_key

        for adjacent, weight in graph[current_node].items():
            if adjacent in keys and weight < keys[adjacent]:
                keys[adjacent] = weight
                pi[adjacent] = current_node

    return mst, total_weight
```
